---
title: "Squeezebox/Logitech Media Server"
date: 2014-06-20
forum: Multimedia Software
---

### Post by m9ke2 on 2014-06-20
Ran Squeezecenter on 10.04 for a couple of years, driving 4 separate Squeezebox hardware devices.  Not a small investment in the HW.

Upgraded to Xubuntu 14.04.  Discovered when attempting to re-install the server that Logitech has stopped supporting my Squeezeboxes.  They now offer a Logitech Media Server, which I tried to install with out success.

My hardware is a 32-bit HP desktop, 4GB RAM and lots of disk space.

In looking at the logs for the server, I see it repeatedly starts and restarts every 5 seconds.  Plenty of other people have had this problem, and after investigating it on the net, I tried solutions which seemed to work for others.  No joy there.

My main interest is to be able to use the Squeezebox hardware.  These are cool devices and it's a shame Logitech bailed on them.  

Anyhow I installed Plex but I could not get the Squeezeboxes to connect to it.

So my request is for any ideas on how to get Logitech Media Server working on my Xubuntu box.

Thoughts, anyone?

---

### Post by m9ke2 on 2014-06-29
Problem solved.  Something changed some where that was incompatible with the version of Logitech Media Server I was trying to install.  I suspect but haven't proven that it was an update to Perl.

From
[http://downloads.slimdevices.com/nightly/index.php?ver=7.8](http://downloads.slimdevices.com/nightly/index.php?ver=7.8)


I downloaded 
logitechmediaserver_7.8.1~1402661598_all.deb

Followed the the instructions here:
[http://www.cyberciti.biz/faq/ubuntu-linux-how-do-i-install-deb-packages/](http://www.cyberciti.biz/faq/ubuntu-linux-how-do-i-install-deb-packages/)

Specifically this part:
[h=3]Install all packages from /nfs/pkgs/ubuntu-builds directory[/h][COLOR=#111111][FONT=Arial][COLOR=#993399]Recursively handle and install all regular files[/COLOR] matching pattern *.deb found at/nfs/pkgs/ubuntu-builds/ directory and all of its subdirectories, type:
$ sudo dpkg -i -R /nfs/pkgs/ubuntu-builds/[/FONT][/COLOR]
I chose that version because it showed a Perl update for Perl  5.18

On my box perl -v returned
This is perl 5, version 18, subversion 2 (v5.18.2)

---

