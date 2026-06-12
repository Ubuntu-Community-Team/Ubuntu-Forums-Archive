---
title: "Ubuntu.8.10  -I can see my neighbours wireless connections -but not my own !"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by pjnsmb on 2009-01-20
I have an Acer 2575 Laptop linked to the internet with a Netgear router and WPA2 Security.

This works fine on wireless whilst running an  installed Ubuntu 8.04.1  :D

I am being a little cautious because of the amount of people with wireless problems after updating that I see on the forum............

So -when I run the live CD of Ubuntu 8.10 to test it before I either update 8.04.1 or reinstall as 8.10 I cannot connect to my own wireless connection !  :(

When I look at the  Wireless Networks applet  I can see a few close neighbours available connections -but not my own !  :o


If I try to connect to a hidden wireless network with my details, and also fill in the Default Keyring the connection screens disappear and the attempt goes nowhere.

If I look in the Passwords and Encryption Keys I can see a Network secret for my input and the password shows as a multi figured and lettered string.


If I try to create a new network connection with my details I still get nowhere and remain unconnected.

If I try to create a new connection without security my connection appears on the applet list without a signal strength but when I try to connect I get as far as the two green lights showing on the applet but immediately disconnecting.

I can connect wired to both 8.04.1 and 8.10 live CD without a problem..............

I cannot find anyone else with this problem - might be easier to solve if I could not see any connections at all- and no I do not want to use the neighbours connections- the signal strength and security stop me !

As I seem to be fine with all hardware and wireless card working properly on the installed 8.04.1-and can see connections on 8.10 I will not submit any further info unless requested to.

Bit of an unusual one I think.......................

Any of you experienced users got any advice or ideas please ?

---

### Post by pjnsmb on 2009-01-22
bump please

anyone any ideas ?

thanks

---

### Post by Sticky on 2009-01-22
No ideas to help but I am experiencing similar problems with one of my laptops, a Dell Inspiron which my wife uses.  I also have an Acer laptop which I use and I have no problems connecting with this one.

This problem has only occurred since I upgraded to Intrepid.  Everything was fine with Hardy.

Any thoughts anyone?  At the moment I'm seriously considering doing a clean Hardy install on the Dell again.

---

### Post by danni-la on 2009-01-22
both my brother and I had this problem the wireless network we were trying to connect to was 'hidden' and the only way to connect properly to it was to set it to visible again and now there are no problems, I realize this won't be everyone's preference but it worked for us.

---

### Post by dca on 2009-01-22
Same here, can only connect on an Acer laptop (using modded ath_pci) to non-hidden SSIDs...  I'm leaning towards it being a NM issue because this ath_pci driver (ath5k & ath9k aren't reliable) worked fine for 8.04 & openSUSE 11.0.  Haven't tried it on F10 or OS11.1...

---

### Post by pjnsmb on 2009-01-25
Problem solved at last !  .....................

After days of trying and much forum searching and 'googling' I came across this website :


[http://www.ubuntugeek.com/ubuntu-hardyintrepid-intel3945-wireless.html](http://www.ubuntugeek.com/ubuntu-hardyintrepid-intel3945-wireless.html)


Halfway down the page I saw :

"If you are in Europe and using a European only wifi channel (such as channel 12 or 13) note that Intrepid by default does not use these channels.

 It is US by default regardless of your region.

 You need to add the following line to /etc/modprobe.d/options :

options cfg80211 ieee80211_regdom=”EU”

Answer =

I changed my Netgear router to channel 8 from channel 12 and connected straight away !

---

### Post by dca on 2009-01-26
Hmmm, I'm in the US, I'll have to look at my settings...

---

### Post by Byb on 2009-12-20
Hi all
I hope I can post this here without disturbing as I could not get help elsewhere.
I have this problem too now I installed eeebuntu3 over the eeebuntu2. 
The new kernel is ```
Linux 2.6.29-1-netbook #0array1 SMP Mon Feb 23 15:02:03 MST 2009 i686 GNU/Linux
```I reapplied the
options cfg80211 ieee80211_regdom=EU
line in /etc/modprobe.d/options file and now nm can see the SSIDs on 12/13 channels, but I can't connect to them (or only after several trials and resending the WPA2 password, although a little faster without wireless encryption).
When connected the throughput is very poor, only ping -s1 get seldom replies from the AP or more remote IPs, when ping -s2 will never get replies.
Other devices can easily connect the AP and have good connection.
I posted a lot of info [here]("http://forum.ubuntu-fr.org/viewtopic.php?id=365751") on the french forum and [here]("http://forum.eeebuntu.org/viewtopic.php?f=42&t=4768&p=22643#p22643") on the eeebuntu one, but I could not get help and I found nothing in google about that.
If you want to help me, do not hesitate to ask more info (like translating the french page)
Thank you

---

