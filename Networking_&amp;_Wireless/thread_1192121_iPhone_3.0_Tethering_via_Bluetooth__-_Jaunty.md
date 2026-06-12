---
title: "iPhone 3.0 Tethering via Bluetooth  - Jaunty"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by SupaRice on 2009-06-19
Fresh install of Jaunty on my Dell Mini9, the laptop sees the iPhone and the iPhone sees the laptop.  If I choose automatic passcode, the iPhone says "check to see if passcode xxxxx is displayed on your computer" then there are cancel and pair button options.  Jaunty doesn't display anything, and I click "pair" on the iPhone and then it fails.  If I choose to issue a manual passcode in Jaunty, the iPhone shows a completely different one that has one more digit longer than what you can manually enter in Jaunty.

I've searched but not seen anything aside from a few google results of Flicker screen captures of people that have it working.

What am I doing wrong?

---

### Post by noisebeard on 2009-06-23
I'm having the exact same problem on a Lenovo S10 with a bluetooth dongle.  Laptop sees the iPhone but refuses to pair.

Any help would rule.

---

### Post by dimension6 on 2009-06-28
Try installing bluetooth-manager ```
sudo apt-get install blueman
``` and using that GUI instead. It provides more options for tethering the iPhone, and I was able to successfully pair it and tether on Softbank (Japan). You may have to run bluetooth-manager as root for tethering to work. Let me know if this works. I only tested it out once.

---

### Post by zeus.jay on 2009-06-29
Hi I can confirm dimension6's suggestion works.

However you'll need to edit your sources list

```
sudo vi /etc/apt/sources.list
```

add the sources for your distro from 
[https://edge.launchpad.net/~blueman/+archive/ppa](https://edge.launchpad.net/~blueman/+archive/ppa), 

(seems to support jaunty, intrepid, hardy and gutsy)

Once the sources is edited and saved.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install blueman
```

To pair the phone I just clicked the bluetooth icon, clicked find and once iphone was there I chose bond.

Once done you can right click the iphone and say network connections -> connect.

---

### Post by pavera on 2009-06-30
I am having an issue with blueman... I installed blueman, I am able to pair with the iphone, but when I click "network access" I get an error.

"Device added successfully but failed to connect"

any ideas there?

---

### Post by dannyboy79 on 2009-07-01
i have a 2G iphone running 3.0 but I can't even get hardy heron (using the ppa mentioned above) to connect . this is the error I get.

[[IMG]http://img27.imageshack.us/img27/6616/screenshot2pfc.th.png[/IMG]](http://img27.imageshack.us/i/screenshot2pfc.png/)

any help would be appreciated

---

### Post by steveneddy on 2009-07-01
This may help:

[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

---

### Post by dannyboy79 on 2009-07-02
> **steveneddy said:**
> This may help:

[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

nope, that didn't do it either. this is really disappointing. I really wanted to tether internet over bluetooth with my iphone!!

---

### Post by steveneddy on 2009-07-02
Did you lookit dis?

[http://ubuntuforums.org/showthread.php?t=1195655](http://ubuntuforums.org/showthread.php?t=1195655)

---

### Post by dannyboy79 on 2009-07-02
> **steveneddy said:**
> Did you lookit dis?

[http://ubuntuforums.org/showthread.php?t=1195655](http://ubuntuforums.org/showthread.php?t=1195655)

i did look at that but that guide is for Jaunty and it has a dependency of bluez-compat and that package isn't in Hardy Heron. I may still give it a shot but I don't have a wireless adapter on my Ubuntu desktop so maybe this won't even work at all?

---

### Post by steveneddy on 2009-07-03
> **dannyboy79 said:**
> i did look at that but that guide is for Jaunty and it has a dependency of bluez-compat and that package isn't in Hardy Heron. I may still give it a shot but I don't have a wireless adapter on my Ubuntu desktop so maybe this won't even work at all?

To tether using Bluetooth you MUST have a Bluetooth adapter of some kind installed.

Bluetooth is a WIRELESS way of tethering hardware or moving data around without a physical tether.

Bluetooth earpeice for you cell phone? wireless

So, yes, you will need a Bluetooth adapter to pick up the Bluetooth radio from the phone.

---

