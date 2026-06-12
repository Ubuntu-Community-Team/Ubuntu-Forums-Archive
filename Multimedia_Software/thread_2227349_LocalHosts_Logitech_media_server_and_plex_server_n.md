---
title: "LocalHosts Logitech media server and plex server not working since update to 14.04"
date: 2014-06-01
forum: Multimedia Software
---

### Post by hellchico on 2014-06-01
Hi Everybody,
Since I've updated to Ubuntu 14.04, my media servers, Logitech media server and plex server, have stop working. I've tried all updates, install logitechmediaserver 7.8, etc... Still not working despite everything I tried from forum advises... :confused:
Can someone help me? :(

---

### Post by m9ke2 on 2014-06-28
hellchico,  same problem here with logitech media server.  plex works for me but i installed it after the upgrade. I posted a request for help but got no replies.

Like you I worked on it and did a bunch of searching on the net, but so far have not solved this puzzle.  I looked at the logs for LMS and found that it was starting, dying, and restarting every 5 seconds or so.  

I uninstalled the software since then, but IIRC the logs are at /var/log/logitech media server.  if you want to check your logfile for the server, maybe we are having the same problem.

Anyway let me know.

m9ke2

---

### Post by m9ke2 on 2014-06-29
Problem solved.  Something changed some where that was incompatible with the version of Logitech Media Server I was trying to install.  I suspect but haven't proven that it was an update to Perl.

From
[http://downloads.slimdevices.com/nightly/index.php?ver=7.8](http://downloads.slimdevices.com/nightly/index.php?ver=7.8)


I downloaded 
logitechmediaserver_7.8.1~1402661598_all.deb

Followed these the instructions here:
[http://www.cyberciti.biz/faq/ubuntu-linux-how-do-i-install-deb-packages/](http://www.cyberciti.biz/faq/ubuntu-linux-how-do-i-install-deb-packages/)

Specifically this part:
[h=3]Install all packages from /nfs/pkgs/ubuntu-builds directory[/h][COLOR=#111111][FONT=Arial][COLOR=#993399]Recursively handle and install all regular files[/COLOR] matching pattern *.deb found at/nfs/pkgs/ubuntu-builds/ directory and all of its subdirectories, type:
$ sudo dpkg -i -R /nfs/pkgs/ubuntu-builds/[/FONT][/COLOR]
I chose that version because it showed a Perl update for Perl  5.18

On my box perl -v returned
This is perl 5, version 18, subversion 2 (v5.18.2) 

If I were you i would open up a terminal and check your version of Perl.  Just put in perl -v 
If you get similar results to mine, I suggest you install LMS version 7.8 or higher.

That's what worked for me.  Good luck!

---

