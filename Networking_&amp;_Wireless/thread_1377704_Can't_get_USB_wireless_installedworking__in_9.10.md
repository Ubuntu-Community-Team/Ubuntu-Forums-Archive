---
title: "Can't get USB wireless installed/working  in 9.10"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by gsmith45 on 2010-01-10
I've bought an RALINK getnet Wireless USB adapter and am trying to get it to work on a dual boot pc running XP and 9.10.  According to the forums and the manufacturers website ([www.getnet.com.tw](www.getnet.com.tw)), this should be supported in Linux.   

Using the disk that came with it, I have gotten it to work in Windows.  I've spent nearly a day scouring the Ubuntu forums and trying different things, but still haven't got it working in 9.10.  (I think that most of my confusion is that many of the threads are for earlier versions)

If I type "iwconfig", I get this:

```
graeme@graeme-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

.... so I'm assuming that the system can detect my wireless card.  

I have the CD that has a LINUX directory, but am not sure what to do with it.  Through other threads I have determined that my drivers are rt2870.sys and .inf and have downloaded these.  I'm not really sure what to do with them next..... Many threads talk about going System>Administration>Networking, but I don't have this as an option.  I have however got an option which I downloaded called "Windows Wireless Drivers" which seemed to let me load the rt2870.inf driver, but then says "No" after it (not very helpful).

I have enabled Wireless Networking, and added my SSID etc etc, but I still don't connect.  

Can anyone advice on what to do next?
Gra

---

### Post by gsmith45 on 2010-01-12
Any thoughts anyone?

---

### Post by changingstate on 2010-01-12
I'll bite. What's in the CD's linux directory?

---

### Post by gsmith45 on 2010-01-12
Thanks.

There's a whole bunch of files and directories in the Linux directory on the CD.   Lots of *.c files, *h files and some makefile type files.

 I was struggling to find a way to list them all here, however I can see that they're all online at the manufacturer's website.  Would you be able to go to 

[http://www.getnet.com.tw/products_GN-331U.html](http://www.getnet.com.tw/products_GN-331U.html) 

and select the Linux option to get the rar archive.  As far as I can tell, this is the same stuff I've got on the CD.  (Or let me know how to post a directory listing with multiple sub dirs!)

If you could help me, i'd really appreciate it!
G

---

### Post by changingstate on 2010-01-12
Ok, as expected, it's the rt2870sta driver. There's a lovely guide here : [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

It's really, really easy to follow, yes? :twisted:

Firstly, your computer is showing a wireless card that appears active on the system. Could you please run : 

```
sudo lshw -C network
```in a terminal and post the results to let me know what's going on there. This should also let me know if the machine has/can get a wired connection to the net, which is probably going to come in very handy, if we can get one.

I've grabbed the driver and had a read through the instructions. I'm going to need to know what country you're in to start setting this up for you correctly. If you could also copy the folder over to your computer, that'll be great, I might have to give you a hand installing this. 

Let's leave it, there, for the moment.

---

### Post by gsmith45 on 2010-01-13
Hi Changingstate. Thx for your help and for taking the time to research the files I was referring to.  If - however - you can read this then I'm wireless!

Thanks for the tip about the other thread.  I read through it and was a little lost after only several pages :-|. However I did try the first part about blacklisting some of the drivers. I couldn't see it made any difference really even after a re-boot.  One thing I noticed was that some related threads talked about the "Network Manager".  I couldn't find this utility anywhere obvious, so what I did in the end was install WICD using 

sudo apt-get install wicd

As soon as WICD started running it showed me a panel where I could actually see the wireless networks around me.  After that it was a fairly straightforward matter of getting the right encryption and re-authorising the MAC address on my router so that I could get connected. So far it seems to work just fine although it does seem to take an extra couple of minutes for the driver to connect itself after booting.

I'm not sure whether it was the blacklisting of the drivers, or whether it was WICD that made the difference.  But thank you for pointing me in the right direction.

G

---

### Post by corruptor1972 on 2010-05-01
I eventually got this USB stick to work with the network-manager that comes with Ubuntu (10.04 - lucid), no need to use WICD.

[I followed the link above]("http://ubuntuforums.org/showthread.php?t=1342593") and carried out the instructions in 'To use rt2870sta and blacklist rt2800usb'.

After that I could connect to the wireless network unencrypted, or with a 128-bit Hex key.  I could not get encryption to work with a WEP Passphrase or WPA/WPA2.

So, for me, it worked but it didn't.  I suppose any encryption is better than no encryption, even if it is only wep.

---

