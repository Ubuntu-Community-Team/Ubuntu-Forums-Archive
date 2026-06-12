---
title: "Solution: Why File Associations don't work on a Network Drive"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by practic on 2009-08-04
I'm posting this as a possible solution to others who may have had a similar problem...I found some other posts from the past that raised the question but there were no answers given, so here's what worked for me.

The Problem
You set up a new computer with Ubuntu (in my case it was an Acer AspireOne Netbook with Jaunty), and define custom programs for media (such as VLC for videos, etc.) Then you browse to a network share (via Samba), double-click a video file (for example), and it launches in Totem. You then right-click the same file and choose Open With (there is not the usual list of other possible apps, so you have to pick one from the scrollable list). You pick VLC, and the application opens, but no file loads. Similar problems are experienced with other files (OpenOffice docs want to load in Archive Manager, etc).

Right-clicking the file, choosing Properties, and editing the Open With options does nothing...in fact the file is already set to open with the user-defined app...it is just ignored.

The Solution
I knew it was a problem with something in my installation, because I had other computers running Ubuntu on the network that worked just fine. So I opened Synaptic on both computers, looked at the installed apps, and made a list of those that were missing from the Netbook installation.

I came up with about 2 dozen that were missing from the Netbook, but the one I thought most likely, and which seemed to solve the problem was this one: gvfs-fuse.

After installing gvfs-fuse, and then rebooting (this is necessary), network files now launched with the user-defined applications.

If you have the same problem, try this, and post your experience.

---

### Post by feistybird on 2009-11-10
Thanks for sharing this information.  It really solved my problem.

Although the gvfs-fuse is already installed in my case, but Nautilus is still not opening files in my smb:// folders with my predefined file associations, instead, it insists to install additional software to open .xls, .doc, .pdf and etc... in my smb folder.

I then find that the ~/.gvfs folder is owned by root which might have caused the problem, as I was doing backup & restore of my home directory, and perhaps the permission was not restored properly.  The problem is resolved after I deleted the ~/.gvfs and re-login.

---

