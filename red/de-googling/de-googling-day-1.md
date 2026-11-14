---
icon: envelope
---

# De-Googling, Day 1: Moving to Proton

Today I started moving away from Google and committed to the full Proton suite. I had paid for a full year of a family plan, so it made sense to consolidate everything there instead of paying for overlapping services.

## What I did

### 1. Set up Proton and locked it down

* Created the account on a shared family plan.
* Turned on two-factor authentication and set up recovery options.
* Made sure the account was secure before importing anything.

### 2. Migrated mail from Google

* Used Proton's Easy Switch to import my old mail and labels.
* The import brought over years of backlog, so the inbox was noisy.

### 3. Cleaned up the inbox

* Created folders for the recurring mail: job alerts, tech services, courses, reading and shopping.
* Wrote a Sieve filter that sorts those senders into folders automatically.
* Archived the backlog so only people, government services and the rental agency stay in the main inbox. Nothing was deleted.

{% hint style="info" %}
Sieve only affects new mail, so old mail has to be tidied by hand.
{% endhint %}

### 4. Moved my passwords to Proton Pass

* Migrated my logins from 1Password into Proton Pass.
* Reset passkeys on the accounts that supported them.
* I still have 1Password and NordVPN installed for now. The plan is to retire them and use Proton Pass and Proton VPN instead.

### 5. Fixing the Brave extension issue

The Proton Pass extension in Brave refused to turn on biometric unlock. It reported that the desktop app was not installed, even though the app was installed, signed in and on the same version as the extension.

**What was going on**

The extension talks to the desktop app through a browser feature called native messaging. For that to work, the app has to leave a small connection file in the browser's own folder. Brave's folder was completely empty, and a search of the whole machine showed the app hadn't registered itself with any browser. The extension therefore had no way to find the app.

**What I tried first (didn't fix it)**

* Quitting and reopening both the app and Brave, in different orders.
* Reinstalling the desktop app from the official download, after removing a package-manager copy.
* Reinstalling the extension from the Chrome Web Store and updating Brave.

**What fixed it**

1. Check Brave's native messaging folder to confirm it was empty.
2. Create the missing connection file by hand. It names the Proton Pass host, points to the helper program inside the desktop app, and lists the extension IDs that are allowed to use it.
3. Confirm the helper program inside the app is executable.
4. Leave the desktop app running, fully quit Brave, reopen it, and enable biometrics again.

{% hint style="info" %}
The file is a single small JSON file, so it's easy to undo by deleting it. I've left the exact contents out of this post.
{% endhint %}

If you hit the same error, it's also worth reporting to Proton Support, since the app should create that file itself.

## What I learned

* Do the security setup first, then import.
* Folders and labels can't share a name in Proton.
* Filters are for the future; cleaning the backlog is a separate job.
* "App not installed" in a browser extension often means "can't reach the app", so check the native messaging folder.
* Paying for a bundle is a good reason to actually consolidate.

## Next

* Move calendar and contacts.
* Replace Google Drive and Photos.
* Retire 1Password and NordVPN once everything has moved.
* Move remaining accounts off "Sign in with Google".
