---
title: "Wireless working on livecd but not on install"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by lolara on 2010-11-25
When I run Kubuntu on livecd everything works perfectly, I just click on systray icon, select my network, enter wpa pass and it's all setup! But after I installed Kubuntu on HDD it doesn't work like that anymore. 
[http://i53.tinypic.com/2cftyzk.png](http://i53.tinypic.com/2cftyzk.png)

Version 10.10. Maverick Meerkat

---

### Post by grahammechanical on 2010-11-25
What is missing or not working like that anymore? Do you have a network manager icon? Can you see a list of available wireless networks? Is networking and wireless enabled? You are using a laptop. Is there a hardware switch that you need to set to activate wireless in the laptop?

The fact that things work when using the live CD proves that there is not a problem with Ubuntu recognizing the wireless device or with connecting to the router/modem.

Your post sounds like a complaint instead of a request for help. We need to know what you are seeing or not seeing as you try to connect.

Regards.

---

### Post by lolara on 2010-11-25
> **grahammechanical said:**
> What is missing or not working like that anymore? Do you have a network manager icon? Can you see a list of available wireless networks? Is networking and wireless enabled? You are using a laptop. Is there a hardware switch that you need to set to activate wireless in the laptop?

The fact that things work when using the live CD proves that there is not a problem with Ubuntu recognizing the wireless device or with connecting to the router/modem.

Your post sounds like a complaint instead of a request for help. We need to know what you are seeing or not seeing as you try to connect.

Regards.

I told ya, on live CD everything works fine. What changed, well, I posted you a screenshot, I can't see a list of available wireless networks anymore, and networking is enabled (so is wireless too). Hardware switch is on, why would I deactivate it? 
Thanks.

---

### Post by lolara on 2010-11-25
I downloaded and installed updates. After restart, wired connection also doesn't work, it simply says Connection state: Unmanaged for both adapters. What now?
I'm stuck at windows now.. :/

---

### Post by lolara on 2010-11-25
Anyone? It's urgent..

---

### Post by spiky001 on 2010-11-25
Ok what I would do is load cd into software sources, now I dont have kubuntu so not sure where it is on ubuntu it's in System/Administration/software sources if you tick cd at bottom then reload update manager it should load drivers from disc

---

### Post by chili555 on 2010-11-25
First, let's be sure your wireless driver is loaded. In Applications > Accessories > Terminal do:```
sudo modprobe ipw2200
iwconfig
```Do you now have a wireless interface eth1? If so, please run:```
sudo iwlist eth1 scan
```Now can you connect?

If not, let's be sure the kill switch is in the correct place:```
rfkill list all
```What kind of laptop is it?

Depending on these answers, we'll decide how to proceed.

---

### Post by linux-hack on 2010-11-25
Well may be (probably) after install you do updates, so your kernel is updated.That means you don't have the same kernel modules on the installed system as in the live CD. AM I WRONG ? 
 Be sure also that it is enabled in the BIOS.

---

### Post by chili555 on 2010-11-25
> so your kernel is updated.That means you don't have the same kernel modules on the installed system as in the live CD. AM I WRONG ? ipw2200, shown in his tinypic, have been in the kernel since forever.

---

### Post by linux-hack on 2010-11-25
> **chili555 said:**
> ipw2200, shown in his tinypic, have been in the kernel since forever.

Didn't see the screenshot :oops:

---

### Post by lolara on 2010-11-25
> **chili555 said:**
> First, let's be sure your wireless driver is loaded. In Applications > Accessories > Terminal do:```
sudo modprobe ipw2200
iwconfig
```Do you now have a wireless interface eth1? If so, please run:```
sudo iwlist eth1 scan
```Now can you connect?

If not, let's be sure the kill switch is in the correct place:```
rfkill list all
```What kind of laptop is it?

Depending on these answers, we'll decide how to proceed.

Still not working.
[http://i51.tinypic.com/wix3f4.png](http://i51.tinypic.com/wix3f4.png)
Toshiba Satellite Pro M70

---

### Post by chili555 on 2010-11-25
It says 'Unmanaged.' What happens when you click "Manage Connections?' Your wireless driver is healthy.

---

### Post by lolara on 2010-11-25
It opens me network manager where I can create wired/wireless/VPN... connections.
Even if I do, it still doesn't do anything.

---

### Post by chili555 on 2010-11-25
Please do:```
sudo gedit /etc/network/interfaces
```Remove all listings except:```
auto lo
iface lo inet loopback
```Proofread, save and close gedit. Now, restart NM and networking.```
sudo service networking restart
suso service network-manager restart
```Is there any change in the Network Manager icon? If not, reboot and look again.

---

### Post by lolara on 2010-11-25
Whoa! That works! Thanks a lot! :D  
Hope I won't have to do that every time.. :p

---

### Post by chili555 on 2010-11-25
If it doesn't work correctly now, please post back and we'll try to fix it. I'm glad you're back in business.

---

### Post by lolara on 2010-11-26
Yeah, just what I thought, I need to do those steps every time I turn on computer.

---

### Post by chili555 on 2010-11-26
Let's see which exact thing starts it. Reboot. Open a terminal and do:```
lsmod | grep ipw
```Is the module ipw2200 loaded? If so, that's a factor we can eliminate. If not, do:```
sudo modprobe ipw2200
```Does that get the wireless going? If so, we know what we need to do:```
sudo su
echo ipw2200 >> /etc/modules
exit
```If the module ipw2200 was loaded, let's go on to the next step:```
sudo service network-manager restart
```Does that get you going, or does this?```
sudo service networking restart
```Whichever specific step is the key, we can automate. Post back and we'll proceed.

---

### Post by lolara on 2010-11-26
This:
{
```

sudo kate /etc/network/interfaces

```Remove all listings except:
```

auto lo
iface lo inet loopback

```Save and close kate. Now, restart NM.
```

sudo service network-manager restart

```}
Also note, I have to pppoeconf every time I do that, so if you could automate that too, that would be nice. :)

---

### Post by chili555 on 2010-11-26
> This:
{
Code:

sudo kate /etc/network/interfaces

Remove all listings except:
Code:

auto lo
iface lo inet loopback

I don't understand. Once you have made that change, isn't it persistent? I suspect what's really happening is that your pppeoconf settings are not staying. Have you tried to set the details in Network Manager by right-clicking the icon and selecting 'Edit Connections'? Select the DSL tab and putting your username and password there; also check "Connect Automatically.'

Post back and let me know your progress.

---

### Post by lolara on 2010-11-26
Alright, here's the deal. I deleted again everything from that file except those 2 lines, and rebooted, after reboot, wireless worked and connected to my network, but the dsl connection I made, didnt work, it didn't connect, nor it appears in network manager connections where I can just click it to connect, so I had to use pppoeconf again.

---

### Post by chili555 on 2010-11-26
> wireless worked and *connected to my network*, but the dsl connection I made, didnt work, *it didn't connect*,I'm afraid I don't understand. It connected or it didn't connect? Which?

---

### Post by lolara on 2010-11-26
You said that I need to make a DSL connection in network manager and set it to "automatically connect" which I did, and that (auto connect) didn't happen, nor I can 'dial' it. But on the other side wlan works after booting now, I don't have to do those steps again.

---

### Post by chili555 on 2010-11-26
Thank you. I understand better now.

---

### Post by lolara on 2010-11-27
> **chili555 said:**
> Thank you. I understand better now.
So.. what now? :P

---

### Post by chili555 on 2010-11-27
Tell me what pppoeconf commands you run. Obscure or diguise any passwords or unique details.

---

### Post by lolara on 2010-11-27
> **chili555 said:**
> Tell me what pppoeconf commands you run. Obscure or diguise any passwords or unique details.

I simply run pppoeconf, and always hit "Yes" on every question, enter my username and password, again "yes" "yes" "yes".. and that's it.. :P

---

### Post by chili555 on 2010-11-27
I still don't understand. Maybe I'm getting too old; you don't get 7,000 posts in a week!

Evidently, something is connecting and something else is not:> wireless worked and connected to my network, but the dsl connection I made, didnt work, it didn't connect, nor it appears in network manager connections> that (auto connect) didn't happen, nor I can 'dial' it. But on the other side wlan works after booting nowWhat I am reading is 'it works and it doesn't work.' I don't understand.

Is this a DSL modem that you are connected to? With or without a router? Do you have the option to put the DSL username and password in the router?

Or, heaven forbid, is this a dial-up telephone connection?

Is this any help?

[http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10](http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10)

---

### Post by lolara on 2010-11-27
Argh, I need to connect to modem (wirelessly) and then, because modem is set in bridge mode, I need to make a dsl connection to connect. I can set modem to pppoe but I have more usernames and passwords because I don't have flat rate I switch between them.. :P
P.S. The link didn't work.

---

### Post by chili555 on 2010-11-27
> P.S. The link didn't work.Did you try to copy and paste it into Firefox or did you just click it?> have more usernames and passwords because I don't have flat rate I switch between them..If you were using Network Manager to do the hard work, you'd still have to manually edit the various usernames and passwords. I am not sure that running pppoeconf is any less cumbersome.

---

### Post by lolara on 2010-11-27
> **chili555 said:**
> Did you try to copy and paste it into Firefox or did you just click it?
Meh, I wanted to say that the solution doesn't work, sorry.
> **chili555 said:**
> If you were using Network Manager to do the hard work, you'd still have to manually edit the various usernames and passwords. I am not sure that running pppoeconf is any less cumbersome.
Well, in Network Manager I could create more connections and then dial whichever I want, right?

---

### Post by chili555 on 2010-11-27
> Well, in Network Manager I could create more connections and then dial whichever I want, right?It would seem so; what happened when you tried? Did you set them up and then click the NM icon and see them listed and select one? Did it try to connect or just sit there? Any signs of life?

I use PPPoE, but mine's set up in the router, so I am speculating a bit here.

---

### Post by lolara on 2010-11-27
When I create them, they aren't listed in NM.
I mean, they don't show up when I click the icon so I could click on it to dial.

---

