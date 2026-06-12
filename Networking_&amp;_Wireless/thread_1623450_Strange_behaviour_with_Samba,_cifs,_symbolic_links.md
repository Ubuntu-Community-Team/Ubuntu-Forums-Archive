---
title: "Strange behaviour with Samba, cifs, symbolic links and 'unix extensions = no'"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by sm_key on 2010-11-16
Hi,
I'm getting peculiar behaviour with Samba and was hoping someone could help me. I have searched quite a bit but not turned up anything like the problem I am facing. 

I have recently set the 'unix extensions' property on my samba server to 'no'. This was to enable me from my cifs client to 'follow' symbolic links on my server. FYI: my server is iomega NAS drive with a scaled down version of linux on it (Samba Version 3.0.14a).

The good news is that is works fine - I can follow symbolic links! The bad news is that the cifs client on my pc (ubuntu 10.04 64bit) doesn't reflect all the files on the share (cifs Version 1.12-3.4.7).  

The behaviour seems to be quite arbitrary but I am sure there is some kind of pattern. Some directories reflect all files, but never more than 148 files from what I can tell.

Initially I thought this was a problem with the server but then when I accessed the same share from my wifes windows box all the files were available. It might still be server related but there is definitely some faulty interaction with the client at play.

I explored some more... When I removed the 'unix extension' parameter from the NAS server I could see the full complement of files, unfortunately this meant I could not browse the symbolic links. When I added the cifs client attribute 'nounix' in my fstab file then I could browse the symbolic links but couldn't received the full complement of files on the server (again limited to 148 ).

I now have 2 mount points for the same share. The one I use to access all my data across the NAS drive and the other I use to access the part of my NAS server that utilises the symbolic links (I've attached a additional usb hard drive to the NAS device which is why I have the need for a symbolic link) - fortunately none of the folders that are underneath the symbolic link folder have more that 148 files in them!

I'd be really appreciative if someone could show me the light with this issue.
Thanks in advance.

---

