---
title: "Nautilus script to permanently mount a network share?"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by ahood on 2009-08-15
This is a forum thread to solicit feedback from Ubuntu forum community on a proposed solution for Brainstorm idea [**[COLOR="Blue"]#19061[/COLOR]**]("http://http://brainstorm.ubuntu.com/idea/19061/").

**The Problem**
Homes are becoming increasingly network centric, especially with media, and the desire to enable local programs (e.g., music player) permanent access to shared folders/data, which requires advanced Linux knowledge that new Linux users will likely not possess and potentially limit adoption of a great OS environment.

**[B]Why Needed**[/B]
Ubuntu strives to make GNU/Linux easy to use for everyone, not just geeks.

Permanently mounting a network share is not intuitive/easy for new Linux users.

Discrepancy between the ease by which network shares are mounted temporarily (works for noobs and veterans) versus permanently (veterans).

**Proposed Solution**
Create a Nautilus script available from the repository for mounting a network share permanently. User on client machine does the following:

1. Use Nautilus to browse for a network share, but does not open it.

Note: Opening a network share in Nautilus will temporarily mount it.

2. In Nautilus, right-click on network share folder name and select 'Mount Volume Permanently'

3. User is asked to enter administrator password.

Note: Option to not ask for administrator password, but restrict mount point to user home directory.

4. New Mount Volume Permanently window appears (see attached jpeg).

5. User enters path of new mount location, authentication user name and password (see attached jpeg).

Note: share name/IP and share type are automatically retrieved. 

6. User clicks on 'Create' button.

7. A new window appears warning the user that /etc/fstab will be modified and all drives will be remounted with option to cancel or proceed.

8. Script checks for line in /etc/fstab that matches the parameters and if absent, adds new entry, then automatically remounts drives.

9. Remove button warns user and deletes local mount point and disables matching entry in /etc/fstab by adding a hash mark.

**Reasons not to Implement**
Proliferation of entries in /etc/fstab.
Does not teach user the value of the CLI
Redundant with manually editing the CLI
Technically not feasible
Lack of interest by programmers
Better solution available

---

