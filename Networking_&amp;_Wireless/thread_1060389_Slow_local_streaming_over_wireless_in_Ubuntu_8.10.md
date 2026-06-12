---
title: "Slow local streaming over wireless in Ubuntu 8.10"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by sirsmegalot105 on 2009-02-04
I have an Intel PRO/Wireless 3945ABG card in my Acer Aspire 5920 laptop, which I dual boot with Windows XP,

When I browse my samba shares over wireless (hard disks used as media servers), it can take up to a full minute just for the folder contents to appear. You can therefore see that trying to open a video or audio file causes Nautilus to hang.

On ethernet there's no issue, it's just over wireless but the connection is working fine and with 98% signal. Plus in Windows I don't have this problem and streaming of even large video files is not a problem (54mbps wireless so the occassional buffer is expected of course).

Not sure why I'm having this problem, I should mention the samba shares are in the smb://192.168.0.5/sharename format instead of //server/sharename (the latter method doesnt work, browsed a lot on this forum and seen that using the IP resolved it so using that as a workaround).

Thanks for any advice!

---

### Post by sirsmegalot105 on 2009-02-04
Actually.... it is affecting my download speeds too, from the Internet.

I've done some tests by downloading a 1GB file from thinkbroadband.com, on wireless I'm getting around 130-169 kB/s (and System Monitor shows a maximum 200KiB/s under Network History).

When I plug in the 100bmps ethernet cable, the download speed increases to 680-700 kB/s (and Networking History shows 800KiB/s as max). This seems really strange... why is this being affected like this if I'm on wireless? I can download at the exact same full speed of 800kB/s+ on Windows.

BTW I don't want to come across as a "but Windows works!!!" kinda guy, believe me, I've spent days getting Ubuntu all set up and even decided to make it my main OS. I am scratching my head here wondering what is going on.

<gripe>Oh and its funny how when I plug in my Ethernet cable and I have to pause and unpause the Firefox download, in order to get it to continue</gripe> :p

Thanks in advance for any assistance, I'm sure there is something I can do to resolve this issue

---

### Post by sirsmegalot105 on 2009-02-06
Any ideas folks? ;)

---

### Post by wjp.reg on 2009-02-06
Thought my comments might revive your thread ;-)

You didn't mention using any encryption on your wireless connection.  This could slow your transmission, but I don't know by how much.  I also wonder if the performance issue is at all related to your samba setup.

Would it be worthwhile displaying your /etc/samba/smb.conf file here?

Have you set the following parameter as suggested in smb.conf?

```
# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

```

I am running the same wireless nic and have been streaming audio from my ubuntu server with no perceptible delays.  I am, however, disappointed in file transfers which are usually in the range of 2mb/s and 5mb/s, regardless of file size.  In my case, ethernet transfers and internet connections are not any faster.

I have seen a number of threads complaining that intrepid is slower than past releases.

Perhaps there are others who can shed some light on your issues

cheers,

wolf

P.S. I am using WPA Personal (passphrase) encryption on my DHCP wireless router connection with DSL internet service

---

### Post by sirsmegalot105 on 2009-02-06
Thanks for the reply :p

My smb.conf has that line but with a # at the start, which I assume means its "commented out" and not in use.

To be honest I don't think it is specific to Samba. On ethernet I get pretty quick file transfers locally to and from smb shares (set up by IP/sharename).

On wireless, however, browsing these shares takes aaaaages. And as I mentioned before, this also affects my download speeds from the Internet so therefore it would suggest this isn't Samba at fault? (or maybe it is, what do I know hehe :o)

I have pretty much same setup as you on wireless: WPA-PSK (TKIP) security on wireless ADSL router (its actually a secondary "bridge" and I have another router which I use for ADSL and DHCP, though its the same security and issues if I connect to that access point too).

---

### Post by sirsmegalot105 on 2009-02-08
* shameless bump * ;)

---

### Post by sirsmegalot105 on 2009-02-17
* Ahem * Really would appreciate help with this, as would others in the same situation.

I know I'm still a bit of a n00b but I've been doing my research and although others have found solutions to their own wireless issues with the card I have, I'm still having this slow wireless problem (both local and Internet).

---

### Post by plasmab on 2009-04-15
Folk, 

I had a similar issue with video freezing from time to time... 

I discovered that it was samba and winbind fighting and there were domain auth problems. 

Try 

sudo killall winbindd
sudo /etc/init.d/samba restart

and see if that makes any difference

---

### Post by plasmab on 2009-04-15
Also worth looking at this thread 

[http://ubuntuforums.org/showthread.php?t=672517](http://ubuntuforums.org/showthread.php?t=672517)

---

