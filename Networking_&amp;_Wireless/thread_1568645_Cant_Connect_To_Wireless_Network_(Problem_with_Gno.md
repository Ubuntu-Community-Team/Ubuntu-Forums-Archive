---
title: "Cant Connect To Wireless Network (Problem with Gnome Keyring)"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by sir_robert007 on 2010-09-05
I am using an Asus EEE PC 900HD netbook and lately Ive been having trouble connecting to my wireless network (WPA2 secured). The WiFi adapter is a RealTek RTL8187SE. Every time I try to connect Network Manager prompts me for my WPA2 wifi security key, which already happens to be entered in the prompt. I then press Connect but after a while the prompt with the password already entered appears again without connecting to the network. I should point out that this issue only seems to happen on this network. All other networks (including other WPA2 networks) I can connect to with ease. I have MAC address filtering enabled on this network and have the MAC address properly entered in my router and have been able to connect to my network in the past until now. I believe this is a problem with gnome-keyring as I when I first started using Ubuntu on this computer (9.04) I got confused with the whole default password for keyring thing and I messed it up so that every time I connect to this particular network the Network Manager prompt would appear and I would have to press Connect to connect to my network

Steps I have taken include the 8th post here: [http://ubuntuforums.org/showthread.php?t=780544&highlight=cant+connect+to+wifi+network+gnome+keyring]("http://ubuntuforums.org/showthread.php?t=780544&highlight=cant+connect+to+wifi+network+gnome+keyring"). I also tried deleting all my network connections and reconfiguring them to no avail. In my troubleshooting I did make an interesting discovery however. I plugged in a USB WiFi adapter (RealTek RTL8187B) thinking I could at least connect to my network and browse these forums for a solution to this problem. The USB adapter connected to the network and I was able to brose the Internet. I then disovered that I could go into into Network Manager and get the other adapter to connect. I coud then unplug the USB adapter and the other adapter stays connected and works flawlessly.

So how can I get my netbook WiFi adapter to connect to my network automatically?

---

### Post by sir_robert007 on 2010-09-06
Hello? I'm still waiting for a reply.

---

### Post by Dittie on 2010-09-06
I had this problem on my older HP laptop not long ago. What I ended up doing was installing wicd and that solved the problem. Not sure that you've tried that yet or not, but if you haven't, its something for you to try :)

---

### Post by sir_robert007 on 2010-09-06
> **Dittie said:**
> I had this problem on my older HP laptop not long ago. What I ended up doing was installing wicd and that solved the problem. Not sure that you've tried that yet or not, but if you haven't, its something for you to try :)

Yeah I read about WiCd in that other forum post. I'll have to give it a try. Oh I also made another interesting discovery. I found out that if I close the laptop (thereby putting it in standby) and then reopening it and waking it up, the wifi adapter connects to my network without the aid the the USB wifi adapter.

Oh also is WiCd capable of managing wired ethernet connections or is it used exclusively for managing wifi connections.

---

### Post by sir_robert007 on 2010-09-08
Ok I installed WiCd. Now I wish to remove Network Manager. However Synaptic wants to remove lubuntu-desktop wheneverI try to remove Network Manager. Is there a way I can remove Network Manager without losing my lubuntu desktop?

---

### Post by sir_robert007 on 2010-09-11
Hello? Still havent gotten a reply.

---

### Post by sir_robert007 on 2010-09-14
still no reply

---

### Post by cavalier911 on 2010-09-14
Ran into the same issue when I wanted to remove chromium browser.
Here is how it was explained:
lubuntu-desktop is a metapackage,all it does is make sure all desktop application packages get pulled in. It doesn't contain anything in and of itself and is safe to remove.  
Re-install lubuntu-desktop and it's depends before you do a distro upgrade.

---

### Post by sir_robert007 on 2010-11-23
> **cavalier911 said:**
> Ran into the same issue when I wanted to remove chromium browser.
Here is how it was explained:
lubuntu-desktop is a metapackage,all it does is make sure all desktop application packages get pulled in. It doesn't contain anything in and of itself and is safe to remove.  
Re-install lubuntu-desktop and it's depends before you do a distro upgrade.

Sorry for the long reply but i finally got it working. Uninstalled network manager with no problem and WiCd is working great!

thanx!

---

