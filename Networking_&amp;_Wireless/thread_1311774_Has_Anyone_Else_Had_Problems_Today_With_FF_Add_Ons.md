---
title: "Has Anyone Else Had Problems Today With FF Add Ons?"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by tacantara on 2009-11-02
Now that I finally have 9.10 installed (after reinstalling 9.04, downloading all updates, then downloading the upgrade package) I'm starting to get things back to the way they were.  That includes reinstalling all of my favorite Firefox add-ons.  When I try to download add-ons from their website or through Tools>Add-Ons, all I get is an Error 228.  I looked it up, and they suggest increasing the cache size (Advanced settings, network tab) if it's under 1 MB.  It was at a default setting of 50 MB, and I even cranked it up to 100 MB, yet add-ons still don't download.

Does anyone out here know if Mozilla is just having issues on their end, or should I be looking to tweak something else on the browser or on my computer in general?

The browser I'm using is the one that came with the 9.10 distro (FF 3.5.4).

---

### Post by tacantara on 2009-11-03
BUMP

I hoped that the problem was on Mozilla's end, but as of today, I still can't download any add-ons from Mozilla.  I'm beginning to think that this is somehow related to the networking problems in this new version of Ubuntu.

From what I've read, the work-around for 9.10 networking issues is Wicd.  I will install that and post the results to this fourm.  Again, if anyone has any advice on this, I'm ready to entertain suggestions :)

---

### Post by tacantara on 2009-11-03
Wicd was a waste of time.  After I tried to manually configure the IP addresses, etc., I was left with no internet at all (no matter how many different configurations I tried).  Fortunately, I was able to access the repository via Terminal so I could reinstall network manager.

I'm convinced that 9.10 has networking issues on some machines.  Not only do I have a problem downloading add-ons for my FF browser, I also have issues with the web pages themselves.  One minute all is well, the next I'm getting "Port 80" error messages.  I hope that someone has filed this bug already.  If not, I'll be more than glad to.

---

### Post by tacantara on 2009-11-04
The problem wasn't with Mozilla.  It was some configuration settings that needed to be tweaked to allow DNS to work properly.  Here's a summary of what I did, just in case you're having connectivity issues with 9.10:

1. Edit the dhclient.conf file by entering the following into a terminal:

```
sudo gedit /etc/dhcp3/dhclient.conf
```When the document opens, edit the line that starts prepend domain-name-servers to read:

```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```Save and close the file.  Go back to your terminal and open the nsswitch.conf file by entering:

```
sudo gedit /etc/nsswitch.conf
```When the document opens, edit the line hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4 to read:

```
hosts: files dns
```Save and exit the document.  To be on the safe side, I restarted my computer after making the edits.  If you're experiencing connectivity problems, this may be your answer.

---

### Post by mike0020 on 2009-11-05
I'm also having this problem, I just did a fresh install of Karmic and I can't seem to install and addons. Unfortunately the fix did not work for me.

---

### Post by tacantara on 2009-11-05
After editing the files, did you either restart your computer or reset your wi-fi card?

---

### Post by mike0020 on 2009-11-05
> **tacantara said:**
> After editing the files, did you either restart your computer or reset your wi-fi card?

I just restarted my computer and it seems to be working. Thanks :).

---

### Post by Petrik on 2009-11-09
This solution is not just for Wireless, works with wired too.

Just one point. Use your own ISP DNS numbers, don't copy them from above. I suspect they will not be too pleased to see a mass increase in traffic.

---

### Post by t0mppa on 2009-11-09
> **Petrik said:**
> Just one point. Use your own ISP DNS numbers, don't copy them from above. I suspect they will not be too pleased to see a mass increase in traffic.

The addresses above offered by tacantara are those of [OpenDNS]("http://www.opendns.com/") and they would probably be rather happy to see a massive increase in their traffic, since they do have a business built around it.

---

### Post by rizitis on 2009-11-12
> **tacantara said:**
> The problem wasn't with Mozilla.  It was some configuration settings that needed to be tweaked to allow DNS to work properly.  Here's a summary of what I did, just in case you're having connectivity issues with 9.10:

1. Edit the dhclient.conf file by entering the following into a terminal:

```
sudo gedit /etc/dhcp3/dhclient.conf
```When the document opens, edit the line that starts prepend domain-name-servers to read:

```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```Save and close the file.  Go back to your terminal and open the nsswitch.conf file by entering:

```
sudo gedit /etc/nsswitch.conf
```When the document opens, edit the line hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4 to read:

```
hosts: files dns
```Save and exit the document.  To be on the safe side, I restarted my computer after making the edits.  If you're experiencing connectivity problems, this may be your answer.

@mike0020 it works, but you have to uncomment the "prepend domain-name-servers" line ;)

---

### Post by lex.online on 2009-11-14
Thank you very much. I've had this problem for weeks and now I finally I fixed it :D

---

### Post by raynman on 2009-11-18
This worked for me but, I had problems with my laptop when I plugged into a network at a different location. Do I need to comment the prepend line out when I change my network?

---

### Post by allmarchri on 2009-12-27
yes it works but I spent along time trying to get this solution to work and only got it to work after I saw from rizitis that you have to uncomment the "prepend domain-name-servers" line.

Thanks Thanks Thanks

---

