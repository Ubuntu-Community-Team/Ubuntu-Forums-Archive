---
title: "Don't know how to connect to wireless broadband"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by KevIreland on 2011-01-03
Hi,

I downloaded Ubuntu 10.04 yesterday using the WUBI thing, once desktop opens in Ubuntu, it's not showing me any wireless connection, but if I restart the laptop and use Windows 7, my connection works fine.

The reason for downloading Ubuntu is that something is wrong with my graphics when using Windows 7 and I can only use it in safe mode now, hence wanting to use Ubuntu, but no wireless connection is showing.

I know virtually nothing about computuers, and having a read around on Google about conenction problems in Ubuntu is doing my head in a bit as I don't know what to download, or how or where to download it to in order get things working, I don't have internet connection when in Ubuntu, so can only use safe mode in Windows if there's something I need to download to get it working?

Any help would be much appreciated.

PS, please keep any explanations simple, otherwise I wont have a clue what you are talking about :)

---

### Post by dandnsmith on 2011-01-03
> **KevIreland said:**
> Hi,
I downloaded Ubuntu 10.04 yesterday using the WUBI thing, once desktop opens in Ubuntu, it's not showing me any wireless connection, but if I restart the laptop and use Windows 7, my connection works fine.

The reason for downloading Ubuntu is that something is wrong with my graphics when using Windows 7 and I can only use it in safe mode now, hence wanting to use Ubuntu, but no wireless connection is showing.


First are we talking about one machine (refs to desktop and laptop might indicate two)?
What would the wireless be talking to? A router?

What does the networking icon (collection of various height vertical lines in the upper RHS) show? If you right-click on it does it offer any networks to connect to? (you'll need to supply password, having selected the network)

---

### Post by KevIreland on 2011-01-03
Hi Derek, thanks for the reply,

> **dandnsmith said:**
> First are we talking about one machine (refs to desktop and laptop might indicate two)?
What would the wireless be talking to? A router?

No, it's just a single laptop, by desktop, I just meant once you have logged in to Ubuntu you are on the main desktop screen, the one that's usually full of icons on Windows.

> **dandnsmith said:**
> What does the networking icon (collection of various height vertical lines in the upper RHS) show? If you right-click on it does it offer any networks to connect to? (you'll need to supply password, having selected the network)

There were no networks showing at all under the networking icon, but if I restart the computer and load Windows instead of Ubuntu, I have my usual wireless connection.

---

### Post by Bucky Ball on 2011-01-03
Have you plugged in an ethernet cable and updated? If you need firmware or drivers for your particular card these should be offered to you when you update (or possibly as soon as you get online).

It would be really helpful if you could let us know what card you have. If you could open a terminal (Applications->Accessories->Terminal) and type in this command:

```
lspci
```

... then look for your network controller. Line should look something like this and be toward the end of the readout:

```
03:00.0 Network controller: **Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)**
```

My card is in bold. Welcome to the forums and let us know.

---

### Post by KevIreland on 2011-01-03
Hi Bucky Ball,

> **Bucky Ball said:**
> Have you plugged in an ethernet cable and updated? If you need firmware or drivers for your particular card these should be offered to you when you update (or possibly as soon as you get online).

I plugged an ethernet cable in yesterday, but it still wouldn't load FireFox browser. Not sure what you mean by updated, as nothing happens when I plug the ethernet cable in, update what where?

**[edit]**

If it's important with regards to what the laptop has on it, it's a **HP Pavilion dv7-4020sa** laptop

---

### Post by KevIreland on 2011-01-03
> **Bucky Ball said:**
> It would be really helpful if you could let us know what card you have. If you could open a terminal (Applications->Accessories->Terminal) and type in this command:

```
lspci
```

... then look for your network controller. Line should look something like this and be toward the end of the readout:

```
03:00.0 Network controller: **Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)**
```

My card is in bold. Welcome to the forums and let us know.

I'll need to shut the laptop down and restart using Ubuntu to do that, back shortly.

On another note, having read some of the posts on this forum, I see members asking people to enter commands as you have and to copy and paste the output on the forum, some of the outputs are very long posts, how do I copy and paste the result of the commands, as I wont be connected to the internet when I'm using Ubuntu?

---

### Post by ruben_linux on 2011-01-03
it is possible you need some package?
have you installed network-manager, wpa_supplicant?
check your versions?

apt-show-versions network-manager

if you need install some package:

sudo atp-get install package

---

### Post by Bucky Ball on 2011-01-03
Good question. You could copy from the terminal to an Open Office word document, save it as a Word doc (not the default Open Office .odt), then paste it from that to the forum. BUT, you could just write down the details of your card that look like the details of mine I have highlighted and report back without going through the copy/paste roundabout. ;)

If you plug in an ethernet cable in Ubuntu that should get you online anyhow. 

You should have Firefox browser and Open Office and everything else if the install has gone to plan. If you DON'T have Firefox, I suspect something has gone pear shaped.

---

### Post by KevIreland on 2011-01-03
> **ruben_linux said:**
> it is possible you need some package?
have you installed network-manager, wpa_supplicant?
check your versions?

apt-show-versions network-manager

if you need install some package:

sudo atp-get install package

Sorry, I don't know what any of that means or how to do it, simple stuff and instructions please :)

---

### Post by Bucky Ball on 2011-01-03
The things he mentions should be installed anyhow, and this is what I'm beginning to wonder. Do you have a network icon in the top taskbar?

I would work off an ethernet cable in Ubuntu while we sort this if that is possible. :)

When you are online, try:

System->Administration->Update Manager

Also, look in:

System->Administration->Additional Drivers (or possibly 'Hardware Drivers' in 10.04).

---

### Post by KevIreland on 2011-01-03
Ok, this is what it says for the lspci command:

**Network Controller: Broadcom Corporation device 4227 (rev 01)**

> **Bucky Ball said:**
> Do you have a network icon in the top taskbar?

Yes, there is a network icon on the taskbar, it has a red apostrophe on it.

> **Bucky Ball said:**
> I would work off an ethernet cable in Ubuntu while we sort this if that is possible. :)

I plugged an ethernet cable in yesterday, nothing happened, still wouldn't connect or load FireFox browser when I tried that.

---

### Post by dandnsmith on 2011-01-03
Under 10.04 my taskbar icon for the wired stuff looks like a pair of arrows (one up, one down, side by side), and hovering over it shows what is connected.

Did you reboot after connecting the wire connection - might make a difference (I haven't tried all the variations yet)

---

### Post by KevIreland on 2011-01-03
> **dandnsmith said:**
> Under 10.04 my taskbar icon for the wired stuff looks like a pair of arrows (one up, one down, side by side), and hovering over it shows what is connected.

I tried the ethernet cable again and now I am connected with the up and down arrows showing on the connection icon, when hovering over the icon it says my connection is called "**wired network connection 'Auto Ethernet' active**"

Although I'm now connected, it's is painfully slow to load pages, but that might just be FireFox, rubbish slow browser that is, I'll install my preferred Opera browser, much quicker and less clunky.

Right then, now that I'm connected, what can I do now to try and get the wireless connection working?

---

### Post by PatchesTheCaveman on 2011-01-03
You'll need to install the Broadcom STA wireless driver or the firmware for the b43 driver for your Broadcom device.  Go to your K Menu/Kicker > System > Additional Drivers.  Alternatively, you can press ALT+F2 and run this command:
```
jockey-kde
```

The Broadcom STA wireless driver or b43 firmware should be available to install from that screen.  If both are available, many people have found the STA driver to work better.  Just click on it, and press Install.  That's all there is to it!

---

### Post by KevIreland on 2011-01-03
@ PatchesTheCaveman, sorry, just seen your post, I installed the Broadcom driver earlier and got the laptop working wirelessly, but it was still taking up to 3 minutes to load webpages even on wireless, whereas on Windows it's very quick, so then I got the hump and uninstalled Ubuntu.

Now I'm back on Windows 7 and I have no wireless connection on Windows which I had before all the time before messing about with Ubuntu :(

---

### Post by PatchesTheCaveman on 2011-01-03
It's highly unlikely Ubuntu did anything to break your wireless card.

Your computer might have come preinstalled with the Broadcom drivers, but now doesn't have them with a fresh installation.  Most computer comes with a driver disc that would have them on it.  You can also download the drivers from your computer manufacturer's website.

If you continue to have trouble, consider asking for help on Microsoft's official forum for Windows support.  They will have people more knowledgeable in troubleshooting hardware issues with that operating system.

[http://social.answers.microsoft.com/Forums/en-US/category/windows7](http://social.answers.microsoft.com/Forums/en-US/category/windows7)

---

### Post by dandnsmith on 2011-01-04
The facts that the wired connection was very slow, the wireless was (?) even slower, and then Windows didn't connect at all suggest to me that there may be a fault to trace in the modem/router or the ISP supply. My bet would be on the router, which is worsening - they can develop faults.

---

### Post by KevIreland on 2011-01-04
> **PatchesTheCaveman said:**
> Your computer might have come preinstalled with the Broadcom drivers, but now doesn't have them with a fresh installation.

When I did the lspci command in the terminal before I had a connection, it said this:

**Network Controller: Broadcom Corporation device 4227 (rev 01)**

Then when I got the connection working with the ethernet cable, I then installed the Broadcom drivers from within Ubuntu, so they probably overwrote my original Broadcom drivers?

> **dandnsmith said:**
> The facts that the wired connection was very slow, the wireless was (?) even slower, and then Windows didn't connect at all suggest to me that there may be a fault to trace in the modem/router or the ISP supply. My bet would be on the router, which is worsening - they can develop faults.

It's definitely not the modem, because my wireless signal/connection was very fast when on Windows 7 before installing Ubuntu, but on Ubuntui the wireless and ethernet connections were both very slow, now that I have uninstalled Ubuntu, my ethernet connection on Windows 7 is now back to as fast as it always was.

Anyway, thanks for the previous help on this topic, it's just a shame that the speed of the connection on Ubuntu was so slow that I was unable to use it, I can't wait for nearly 3 minutes for each web page to load, had the speed been good, I would have used Ubuntu all the time, ah well, live and learn.

Admin/Mods, feel free to lock this topic, cheers.

---

### Post by Bucky Ball on 2011-01-04
> **PatchesTheCaveman said:**
> It's highly unlikely Ubuntu did anything to break your wireless card.


Impossible actually. Not related, two separate partitions, never the twain shall meet, good call Patches.

> **dandnsmith said:**
> The facts that the wired connection was very slow, the wireless was (?) even slower, and then Windows didn't connect at all suggest to me that there may be a fault to trace in the modem/router or the ISP supply. My bet would be on the router, which is worsening - they can develop faults.

Yes. Get into the router configuration page (generally but putting the IP of the router into the address bar of web browser, eg 192.168.0.1 or similar; find out from the router manual if you don't know) and make sure everything there matches what you have on your local machine: SSID (name of router or AP/Access Point), and security key (WEP, WPA, whatever).

Important is to check that you there is no staitic IP set.

---

### Post by PatchesTheCaveman on 2011-01-04
> Then when I got the connection working with the ethernet cable, I then installed the Broadcom drivers from within Ubuntu, so they probably overwrote my original Broadcom drivers?

Drivers are installed on your hard drive, not the wireless card.  They tell the operating system how to talk to your card.  While Windows 7 comes with a lot of drivers, it simply can't have every driver for every device known to man.  Just as an example, Windows 7 came with all the necessary drivers for my Dell Inspiron 1545 except for the touchpad, but had almost none for my mom's HP mini.

Once again, you can usually download all the necessary drivers for your computer on Windows from your computer manufacturer's website.  If you continue to have trouble, feel free to ask on the Windows forum.  They know Windows, we know Linux!

---

### Post by Bucky Ball on 2011-01-04
Solved? Please use 'Solved' in 'Thread Tools'. That is how you can close it. Mods don't 'lock' 'em until they are older when they are archived for future reference. ;)

---

### Post by ruben_linux on 2011-01-06
i´m sorry for my bad post.

:(

---

### Post by Bucky Ball on 2011-01-06
> **ruben_linux said:**
> i´m sorry for my bad post.

:(

Not an issue. Enjoy and 'Buenos noches'. Great you go things sorted. ;)

---

