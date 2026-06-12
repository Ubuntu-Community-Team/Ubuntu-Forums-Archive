---
title: "Atheros AR2413 works weirdly since Natty"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by Lineplus on 2011-04-30
Hello,
When I start my computer, no wireless network is detected, even if I wait a long time. I have to transport my computer in another room, next to my modem: the wireless network is detected, as well as those of the neighborhood, and I can move my computer anywhere, the wireless connection stays and works normally. But the problem backs each time I reboot my computer, or each time I uncheck and recheck “Enable wireless network”. Same problem with Network Manager and Connman.

```
$ sudo lshw -C Network
  *-network               
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:04:05.0
       logical name: wlan0
       version: 01
       serial: 00:19:7d:44:f5:ce
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.0.11 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:c3000000-c300ffff
```Everything was working with Maverick.

---

### Post by truck87bp on 2011-04-30
I currently have EEEbuntu 3.0 on my Asus 1000HE and the Atheros wireless hooks up at 300mps. Testing Unity, I only get 150mps wireless. This needs to be looked into. Note: I loaded Live with a wired hookup. Wired hook up was 100mps.

Also, Unity relies on Compiz for the full experience but does not load from the live CD. Maybe the Live CD should not have any Office installed to save space to allow having Compiz installed. As for the Office problem, create an Icon in the list to point to the software center.

How can you test a machine using the Live CD without the full Compiz experience if its part of the feature of Unity? 

Work Spaces are handled much better in Unity than in Fedora 15 Gnome 3 but should always appear at the top of the Unity Bar.:popcorn:

---

### Post by Lineplus on 2011-04-30
I don't use Unity. The problem seems to be closer to the kernel than to my desktop environment.

---

### Post by PriceChild on 2011-05-01
Hmm I'm also having similar problems with my AR2413. Rebooting into my old (maverick) kernel resolves them. Not sure what to do.

---

### Post by el_koraco on 2011-05-01
It's a kernel issue with ath9, and AFAIK it is being worked on. 
First check that you have ath9 with ```
lspci -k
```


For the rest, I'm gonna repeat myself - this is for Kubuntu, though. Check out the blog post. 

[http://www.jlacroix.me/?p=1999]("http://www.jlacroix.me/?p=1999")

"*Even with Kubuntu being as great as it is, I have a few complaints. The first is the wireless speed. With my Atheros card, it&#8217;s so slow it can take up to five minutes for a page to load, if it loads at all. However, this is not a Kubuntu problem, it&#8217;s a bug with the 2.6.38 Linux kernel and has already been reported, and is being worked on. It&#8217;s easily fixed by adding &#8220;options ath9k nohwcrypt=1&#8243; to the /etc/modprobe.d/ath9k.conf file (that file didn&#8217;t already exist on my system, so I had to create it) and then after a reboot, it was fine. I found that solution here (in post #3). I&#8217;m not sure what all that effects, but it does make things work. Since this bug isn&#8217;t Kubuntu&#8217;s fault, I won&#8217;t hold it against the score, but it was worth mentioning*."

There is also another thread going on - [http://ubuntuforums.org/showthread.php?t=1742274&highlight=atheros+AR928x]("http://ubuntuforums.org/showthread.php?t=1742274&highlight=atheros+AR928x")

You guys need to check for open bugs and start pestering the devs. i have no idea how I was able to escape such issues, seeing as I also use the ath9 driver.

---

### Post by audionut on 2011-05-02
I'm having exactly the same symptoms as Lineplus in post #1. Note, I have ath5, not ath9. It IS the AR2413 chip as well....

NOT having speed problems, just cannot connect unless my laptop is NEXT to the wireless router... once the signal fades down a couple of bars (like going upstairs or some distance from the router), if I reboot, will not connect at all.. or I see the icon "trying" to handshake, but never connects at all...

Any suggestions on how to get back the version 10.10 performance we had before the upgrade would be great. Have tried all the solutions I can find when googling this problem...

Thanks!!:confused:

---

### Post by bl4ckf0xi on 2011-05-02
Hi!

You should follow this instructions and use madwifi driver (for **ath5k natty 11.04**):

```
sudo su
apt-get install subversion
cd /usr/src
svn checkout [http://madwifi-project.org/svn/madwifi/trunk](http://madwifi-project.org/svn/madwifi/trunk) madwifi
tar cfvz madwifi.tgz 
cd madwifi
make && make install
 
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
echo "ath_pci" >> /etc/modules
 
modprobe ath_pci

sudo reboot


```From [http://fossplanet.com/f10/%5Bbug-775104%5D-%5Bnew%5D-kernel-2-6-38-8-ath5k-driver-wireless-signalstrength-critically-weak-148704/]("http://fossplanet.com/f10/%5Bbug-775104%5D-%5Bnew%5D-kernel-2-6-38-8-ath5k-driver-wireless-signalstrength-critically-weak-148704/")

I hope this'll help.

---

### Post by audionut on 2011-05-02
Wow..that seemed to do the trick, bl4ck foxi...

Really appreciate the help!!

Thanks again!):P

---

### Post by rayne127 on 2011-05-19
> **bl4ckf0xi said:**
> Hi!

You should follow this instructions and use madwifi driver (for **ath5k natty 11.04**):

```
sudo su
apt-get install subversion
cd /usr/src
svn checkout [http://madwifi-project.org/svn/madwifi/trunk](http://madwifi-project.org/svn/madwifi/trunk) madwifi
tar cfvz madwifi.tgz 
cd madwifi
make && make install
 
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
echo "ath_pci" >> /etc/modules
 
modprobe ath_pci

sudo reboot


```From [http://fossplanet.com/f10/%5Bbug-775104%5D-%5Bnew%5D-kernel-2-6-38-8-ath5k-driver-wireless-signalstrength-critically-weak-148704/](http://fossplanet.com/f10/%5Bbug-775104%5D-%5Bnew%5D-kernel-2-6-38-8-ath5k-driver-wireless-signalstrength-critically-weak-148704/)

I hope this'll help.

This worked perfectly for me! 

Except that after my first reboot when I attempted to connect to my network Ubuntu froze and went to a black screen with a ton of crazy writing on it. But I shut down and restarted and now it's working just fine!

Thank you!

---

### Post by arkaitzswagman on 2011-05-31
Thanks a lot for this workaround, worked like a charm for me (on a aspire 3610) !:D

---

### Post by pakennedy on 2011-06-17
Ta, fixed my issue too.

---

### Post by PriceChild on 2011-07-22
Seth Forshee has informed me by email that the 'proper' fix for this (not requiring ath_pci) has landed in the -proposed repositories!

---

### Post by aleoo on 2011-08-15
> **bl4ckf0xi said:**
> Hi!

You should follow this instructions and use madwifi driver (for **ath5k natty 11.04**):

```
sudo su
apt-get install subversion
cd /usr/src
svn checkout [http://madwifi-project.org/svn/madwifi/trunk](http://madwifi-project.org/svn/madwifi/trunk) madwifi
tar cfvz madwifi.tgz 
cd madwifi
make && make install
 
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
echo "ath_pci" >> /etc/modules
 
modprobe ath_pci

sudo reboot


```From [http://fossplanet.com/f10/%5Bbug-775104%5D-%5Bnew%5D-kernel-2-6-38-8-ath5k-driver-wireless-signalstrength-critically-weak-148704/](http://fossplanet.com/f10/%5Bbug-775104%5D-%5Bnew%5D-kernel-2-6-38-8-ath5k-driver-wireless-signalstrength-critically-weak-148704/)

I hope this'll help.



apart from this code  
tar cfvz madwifi.tgz

I did all the rest.
One week ago, my problem was the same 
as the other users in this discussion described.
Now I can't detect any wireless network and, when I found your post,
I followed your instructions.
Nothing changed. NM always shows    Wireless network   disconnected   .
I've read that someone changed channel in the router configuration and solved it.
It doesn't work for me..I just tried three different channels, 
I wonder if I have to try them all or it's useless..
I hope to find some help here.
I have an Acer Aspire 3680.

---

### Post by aleoo on 2011-08-16
I don't have [SIZE=2]ndiswrapper installed, is that a problem?
Weeks ago wifi was working (even if weirdly) anyway without it.
[/SIZE]

---

### Post by aleoo on 2011-09-13
Can anyone help me please?

---

### Post by aleoo on 2011-10-30
Same problem with 11.10

---

