---
title: "Diskless client problems"
date: 2008-09-30
forum: Mythbuntu
---

### Post by adam1305 on 2008-09-30
hi all, I have the latest version of Mythbuntu installed, I have been trying get to diskless clients working but keep on getting an error half way through the boot process.  The client successfully connects to the dhcp server, loads the kernel and displays the mythbuntu splash screen.  Shortly  afterwoods I get an error: 

Server Authorization directory .. is set to /var/lib/gdm but is not owned by user ... or group ...

I have looked at the /etc/passwd files on server and client and they are different, is this right and does anyone have any ideas what my problem is?  Interestingly I don't seem able to sudo on the client, although I can read the /etc/passwd file and logon.

Many thanks,

Adam

---

### Post by anonymousdog on 2008-09-30
My passwd files are different too, but it does sound like you've got some issues with your root image or overlay cache.  If removing that diskless client's cache at /var/cache/mythbuntu-diskless/overlay/MACADDRESS/ (on the server while the FE is off, then rebooting the FE) doesn't fix it, it might be best to remove the image, ensure your server is totally up to date (including the mythbuntu-control-centre ~hardy2 fixes release [or a more recent fixes release in case that's not the current offering]) and recreating the image from scratch.  (Else, see the long missive below.)

Troubleshooting tips based on my working diskless system:
There are two areas I'd check based on your symptoms, proper group memberships for your mythfrontend user (and sudoers configuration), and ownership/permissions on your FE's /var/lib/gdm directory.

My /etc/passwd files differ from FE to BE too.  There are some commonalities -- all UIDs 103 and below (so, root through klog), and my mythfrontend user.  The password hashes (in /etc/shadow) on my mythfrontend user are the same on both file systems too.  The frontend /etc/passwd differences are due to different packages/services existing on FE and BE boxes.  Most /etc/group differences are similar to those in /etc/passwd (i.e., caused by differing packages/services on FE/BE)...though I just noticed my mythfrontend user is not in the cdrom group on the diskless file system :confused: (what's up with that, laga?).  My mythfrontend user is also in adm, audio, operator, video, mythtv, and admin groups on the diskless FE file system.  Belonging to the admin group is what allows sudo operations (with password) by default; you can check your FE diskless client's /etc/sudoers file for a line '%admin ALL=(ALL) ALL' which allows sudo ops for admin group members.

My FE's /var/lib/gdm directory is owned by gdm:gdm (i.e., the UID of gdm on the FE, not the BE) and has 0750 permissions.

---

### Post by adam1305 on 2008-09-30
Thanks for your reply, I have tried deleting the overlay cache and the entire image and neither seems to work.  I also tried removing diskless server in the MCC and reinstalling.  Again this didn't work.  

Basically when I create my diskless image it seems to have some configuration issues, but I can't work out what.  

If I log on to the diskless client's shell (X not working as stated previously) there seems to be lots of problems.  Yet in MCC I can bring up the MCC for my image and I can ch root into it.

I did have diskless clients working a week or so ago, but installed some applications on to a client (rather than on server) so thought it best to start again.  I started again by deleting the image in MCC and deleting the overlay folder manually.  The only other thing I enabled since then was the root account.  I am pretty confident that I have cocked something up, I just can't work out what :)

Thanks again for your help,

Adam

---

### Post by laga on 2008-09-30
> **anonymousdog said:**
> up to date (including the mythbuntu-control-centre ~hardy2 fixes release [or a more recent fixes release in case that's not the current offering]) and recreating the image from scratch.  (Else, see the long missive below.)

For the record: +hardy1 is the current release.


adam1305,

can you remove "quiet splash" from the boot options in /var/lib/tftpboot/i386/pxelinux.cfg/default? That should give you more output.

You could also try looking in /var/cache/mythbuntu-diskless/overlay/$MACADDRESS/var/log/.

---

### Post by adam1305 on 2008-09-30
I have removed quite splash as requested and got a lot more info on boot.  How do I read through this information as obviously it scrolled past at a rate of knots (I tried dmesg but couldn't pipe it to more as my keyboard layout changed from UK on boot?)  tried to output dmesg to a file but it wouldn't let me and I couldn't sudo:

sudo: unable to resolve host XXX

I assuming this is yet more symptoms of the problems I am having, I have looked at the /etc/hosts file and it has not been rewritten during the ltsp boot process.  I am sure that all these issues point to one problem but still can't work out what it is,

Thanks again,

Adam

---

### Post by adam1305 on 2008-09-30
I have looked in the /var/cache...overlay directory and interstingly the only contents are:

cow and rofs

I wonder if this may be because I haven't shut the machine down (unable to sudo as mentioned earlier).  I should probably mention at this point that I am using a virtual box as my test platform (I have also tested on a physical client and I get the same results).

Cheers again,

Adam

---

### Post by adam1305 on 2008-10-01
Looking through again I am sure the problem is permissions related.  Could it be anything to do with me enabling the root account?

---

### Post by laga on 2008-10-01
On the client?

Possibly. Try without that option (I assume you were using ltsp-build-client?)

*edit:* I'm referring to root login

---

