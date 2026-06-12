---
title: "Sharing it as a file server over the Internet, securely?"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by Mechphisto on 2013-03-15
This may be an odd question: How would I go about sharing my Linux box over the Internet, securely so that you need a username/password to get in, and have it act like a shared drive?
My first thought was to put an FTP server on it, but I want to be able to stream music and video off of it, as if it were a shared folder on a LAN, and I don't think that's something you can do over FTP?
All my searching on the Web brings me info about SAMBA, which, as far as I can tell, only is good on a networked LAN and not across the Internet.
I also thought of VNC, but the Linux box actually doesn't have an X server, and "controlling" the PC remotely isn't exactly what I need to do... just access it, as if it were a shared folder.

Any ideas what topic, concept, keywords I should search for this?
Thanks!

---

### Post by kuifje09 on 2013-03-15
Anybody aware of any account and a valid passwd on your linux box can use it as a fileserver.
I am not shure if I do understand your question.

From my windown PC's I can access linux with "winscp" a great program if I may say so.
From linux to linux I use "gftp"  which is   "winscp"  alike.

samba or nfs  is meant for a continues "sharing" of files.   with samba even printers.

Hope this helps?

---

### Post by papibe on 2013-03-15
Hi Mechphisto.

There are several steps to accomplish that.

First of all, FTP is very insecure. I'd recommend using sftp, as is both secure (encrypted), and it works out of the box when you install openssh-server.

If you're unfamiliar with that concepts mention below, take a look at this is a very helpul [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

This would be the main steps:
[LIST]
[*]Set your server with a LAN static IP.
[*]Install openssh-server on your server.
[*]Test LAN ssh access to your server.
[*]Optional: change the standar ssh port (22) to a different, preferable higher value.
[*]Subscribe to a Dynamic DNS service. There are free and pay options. For example: DynDNS, no-ip, zoneedit, etc (check [here]("http://dnslookup.me/dynamic-dns/") for a longer list).
[*]Either install and setup the package ddclient, or (better if available) set your DDNS client in your router.
[*]Forward the ssh port in your router to your server.
[/LIST]
Now you are ready to test accessing your server over the internet.

Important: do not try to access your server using its public IP, or dynamic name from inside your own LAN. The proper way to test access is from outside your network. For example, an internet café, public library, a friend house, or using your phone or tablet's 3G service (be sure to NOT being connected to your LAN's WiFi though).

I hope that points you in the right direction, and tell us how it goes.
Regards.

---

### Post by lykwydchykyn on 2013-03-15
If you install openssh-server and make that available to the internet (forward port 22 on your router), you can mount that as a drive from a remote linux box using sshfs.  I don't think Windows can mount over ssh, though you can access the data using WinSCP or Filezilla.

For streaming audio and video, look into mediatomb.  It can be secured with passwords, or you can tunnel it over ssh (you'd need a pretty fast connection, though).

---

### Post by Mechphisto on 2013-03-15
Papibe and.... person with the Welsh-looking name... Thanks! This looks like the kind of info that will do it. I'll start research these steps and concepts. Thanks for pointing me in a direction! :D

---

### Post by lykwydchykyn on 2013-03-15
> **Mechphisto said:**
> person with the Welsh-looking name... 

Sound it out ;)

---

