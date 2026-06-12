---
title: "RTL8187 with WG111v3 still not ok"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by Royke on 2009-12-19
Hello,
When i first installed 9.10 i was glad to see the wg111v3 was working out of the box. There where many network-dropouts but after some updates it seemed to be fixed. It is more reliable now, but not as good as it was before. It is still dropping out occasionally and it won't reconnect. I have to boot 9.04 just to get connection again. The card is operating with 9.10 at 11Mbit/s(max) while it supports 54 Mbit/s. I have a strong feeling that this is the problem, but i don't know how to fix this. 
Please help!

---

### Post by northd_tech on 2009-12-19
[SIZE=2]Hello Royke.

I have heard that the best thing to do is to contact Realtek by email.  See this thread for some info (that Realtek 8187 might be close enough to the 8192SE to work with the same driver):

[http://ubuntuforums.org/showthread.php?t=1347677](http://ubuntuforums.org/showthread.php?t=1347677)

Here is a link to Realtek's website and their contact info:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

[email]wlanfae@realtek.com[/email][/SIZE]

---

### Post by Royke on 2009-12-22
That's something word trying. 
I'll keep waiting for the updatemanager to pop up also ;)

---

### Post by Burky on 2010-01-06
I hear you bro, I have the same problems. It makes me angry. I too would like to know how to fix this.

---

### Post by Burky on 2010-01-08
Royke: Download ndiswrapper and download this [driver]("http://www.avengergear.com/upload/WG111v3.tar.bz2") 
then extract it:
```
tar -jxvf WG111v3.tar.bz2

```

install the driver
```
sudo ndiswrapper -i WG111/WG111v3.inf

```

Enable the driver:
```
sudo modprobe ndiswrapper

```

Then you add "ndiswrapper" to /etc/modules so it will connect at start up, it will looks like this. 
```
  GNU nano 2.0.7             File: /etc/modules                                 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper

```

This worked for me. I get no dropouts and 54mb/s.

---

### Post by Royke on 2010-01-26
Hello,
Mmmmmmmmmmmm, i think i have set it up right this time, but installing ndiswrapper was not the sollution here. And emailing the manufacturers for a driver, well sorry but i leave that up to the ubuntudevelopers unless they need our help for this ;)
Since i am using UbuntuStudio64bit-rt with plain Ubuntu64bit software installed, i realized i had never tried to configure wlan the UbuntuStudio way: just manually and without roaming mode, so i did that. Then i added the UbuntuStudio network applet on the tray along with the Gnome network icon band kept on trying to set up until i saw the Gnome applet searching for connection. Since then it never failed again. I can not imagine but have to believe it is working ok now! It is still working at 11Mbit/s as the gnome tool says and to my experience but i hadn't had a single dropout anymore and network connects before desktop load, like before! Both the dongle and me says that it's ok for now:popcorn:

I still have a question for Burky: did you blacklist the rtl8187?? I tried to install ndiswrapper ( and it is still there) but only for one session it worked, no wlan showed up in networkmanager anymore after reboot, but now that i'm typing i realize i could also config it the US-way i described. I hope this helps a lot of people, because a whole lot of them rely on the rtl8187.

---

### Post by Burky on 2010-01-26
Yeah I'm sorry I didn't specify for 32bit, that's how I got it to work, on the Internet people will claim Ndiswrapper plus WG111v3 will for 64bit but I had no luck. 

That sounds great though it works good for you. Do you have a windows partition though?

---

### Post by Royke on 2010-02-27
Hello Burky,

Yes i have a windows partition but it won't boot anymore. Setting up my pc for real time has killed my windows(finally:D), but it's still there(that virus). I am connected trough a cable now(new isp) and removed the dongle. I will try to keep it that way, but still hope this will be fixed well :KS
I also use 9.04 32bit ubuntustudio(without gnome-networkmanager)and tried your solution for installing ndiswrapper with succes:popcorn: 
Thanks for the help.

---

