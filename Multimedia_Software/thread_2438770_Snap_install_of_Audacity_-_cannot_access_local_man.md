---
title: "Snap install of Audacity - cannot access local manual"
date: 2020-03-17
forum: Multimedia Software
---

### Post by RobotOfBarr on 2020-03-17
It appears that the Snap installation of Audacity is "sandboxed" to the extent that the instructions in Audacity itself to install the local (vs On-line) manual are incorrect. The local install path is /usr/share/audacity/help, when the downloaded manual is installed there, Audacity reports that it cannot be found. This problem is a known to Audacity support.

It would appear (unproven) that Audacity is looking in /snap/audacity/current/usr/share/audacity/help which is read-only and inaccessible (or I've not figured out how to access it).

Can the location where the Snap version of Audacity looks for the manual be restored to the advertised and accessible place? Or can there be a Snap version of the manual that can be invoked from within Audacity as intended?

Synaptic gets it right, the manual when installed at the location given in the instructions (/usr/share/audacity/help) is accessible as intended. I've thrown the Snap version away now and re-installed with Synaptic.

---

### Post by TheFu on 2020-03-17
This is 100% a snap package issue.  Best to open a bug report with that team.
Snaps have so many problems that you may want to avoid them for now.  The file system constraints for any media editors and viewers with snaps are just too restrictive to be useful.  This is a well-know issue with snaps.

snaps, flatpaks and appimages are each an attempt to make portable programs.  I&#8217;ve had failures (crashes) with all of them, which really shouldn't be possible.

---

### Post by RobotOfBarr on 2020-03-18
Thank you for that comment. I appreciate the desire - from a developer's standpoint - for a fully portable distribution/installation mechanism, but the failure in this case to check for a reasonably obvious failing does raise concerns. Those concerns lead to the follow-up question: Why does Ubuntu Software install Snap packages if they are not fully developed to a satisfactory standard?

---

### Post by Autodave on 2020-03-18
I have been using Audacity for over 7 years and have NEVER gotten the manual to work locally: I have always had to access it online.

---

### Post by TheFu on 2020-03-18
> **RobotOfBarr said:**
>  Those concerns lead to the follow-up question: Why does Ubuntu Software install Snap packages if they are not fully developed to a satisfactory standard?

Nobody here can answer that. We don't work for Canonical and our guesses wouldn't be productive.  There are a few other threads in these forums about  snaps which might shed some light on the workarounds and increase understanding.

In my notes, I've kept these URLs, FWIW:
[https://ubuntuforums.org/showthread.php?t=2434651](https://ubuntuforums.org/showthread.php?t=2434651)
[https://snapcraft.io/docs/removable-media-interface](https://snapcraft.io/docs/removable-media-interface)
[https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html](https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html)

However, I find that avoiding and preventing snap packages has worked so far on my 16.04 desktops. Ok, I haven't avoided them completely, but I haven't experienced the ideal results that the techniques are supposed to provide either.  At this point, the main program package that I'll miss because snaps don't work is the chromium-browser.  It is a secondary use-case for me, not my primary browser.  Certain things, like virtual meetings work better in chromium than in my normal browsers (firefox, dillo, lynx).  As support for 16.04 ends, I'm being forced to consider moving to other distros, but not just for snaps.  

Other decisions have broken how Linux works too.  Under the cover changes have been made to LTS releases which aren't supposed to happen.  The way that DNS works has been drastically modified in 16.04 from the way it worked on release.  That is unacceptable.  An LTS shouldn't be introducing completely new packages for core features of an OS in the middle of the release support period.  That's what non-LTS releases are about - alpha testing.

---

### Post by mc4man on 2020-03-18
> **Autodave said:**
> I have been using Audacity for over 7 years and have NEVER gotten the manual to work locally: I have always had to access it online.

Overall this isn't much of an issue, I  bet most use the online manual .
As far as the .deb the extracted folder (manual) has to go into
/usr/share/audacity/help/  folder, help needs to be created..

---

