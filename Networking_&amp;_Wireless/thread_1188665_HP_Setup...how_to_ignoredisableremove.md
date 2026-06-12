---
title: "HP Setup...how to ignore/disable/remove?"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by trekon86 on 2009-06-15
Hey all...
Either I have a family member in my house with a viral SSID or I have a neighbor with an HP printer. We have no HP printers in our house (house from 1700s with 18" thick stone walls) yet I keep getting all sorts of wifi signals. This prompted me to ask here whether it could be a problem (hackers, virus, etc) and how to solve it if it is.
Thanks,
PMZ

---

### Post by MaindotC on 2009-06-16
Post the output of:
```

iwlist scan

```

---

### Post by trekon86 on 2009-06-16
pmz@pmz-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      No scan results

pan0      Interface doesn't support scanning.

pmz@pmz-laptop:~$ 


That's what I got...
PMZ

---

### Post by MaindotC on 2009-06-16
Where are you seeing this viral ssid?  Please embed a screenshot.

---

### Post by trekon86 on 2009-06-16
[ATTACH]117828[/ATTACH]

This is how it appears. I don't know what else it does or whether it's legit or not.
I'm just worried about it.
PMZ

---

### Post by superprash2003 on 2009-06-16
post output of **sudo iwlist scan** , add the sudo

---

### Post by trekon86 on 2009-06-16
pmz@pmz-laptop:~$ sudo iwlist scan
[sudo] password for pmz: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      No scan results

pan0      Interface doesn't support scanning.

pmz@pmz-laptop:~$ 


That's with sudo...
PMZ

---

### Post by MaindotC on 2009-06-17
I saw your picture.  I'm sure you googled this already but just in case I found lots of anomalies with this issue.  Here's an example: [http://www.wlanbook.com/hpsetup-wifi-ssid/](http://www.wlanbook.com/hpsetup-wifi-ssid/)

If I were you I wouldn't waste any time with it.

---

### Post by superprash2003 on 2009-06-27
that seems to be an adhoc network , i think thats what the symbol indicates!!

---

