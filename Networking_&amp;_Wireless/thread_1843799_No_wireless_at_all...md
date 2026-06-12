---
title: "No wireless at all.."
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by stephafrain on 2011-09-14
Hello all, my name is Stephen. I am fairly new to the Ubuntu area and decided just a little while ago to set up Xubuntu on my Toshiba NB505 Netbook. The last time I used Ubuntu was quite a while back on a Notebook I used to share with someone. 

Anywho, I have a problem with enabling my wireless card on this blasted thing. Ive tried installing the driver, which was the process of finding my wireless driver with the .inf extention. I simply didnt even know where to look so I downloaded the original .exe file and changed it to an inf file. I then followed some Ubuntu instructions to install "ndisgtk" which happed to be a 'Windows Wireless Driver" installer, that needed inf files to install with. I tried to install via this program and ended up with an error while installing. It told me something along the lines of "Wrong Driver" or some such. I have no clue if changing the exe to an inf was a no no, I'm still learning in this area of computer technics. 

But for further info, I don't even see any option anywhere to change my network preferences or w/e you want to call it, nor do I see anything that has to even do with wireless networking. All I have is the ethernet connection, which works just fine.

If anyone would kindly help out with this problem I would be extremely thankful. If there are any more questions please feel free to ask. 

Cheers-
stephafrain
-
Stephen.

---

### Post by garvinrick4 on 2011-09-14
Tell the users the Network card you have:
```
lspci -k
```
Just need the Network controller wireless card and driver out of the output copy and paste
to this thread you started.

---

### Post by tommpogg on 2011-09-14
Welcome to the forum.

I am not an expert of drivers and wireless. Anyway, I will give you a suggestion that once it solved my problem: is the On/Off WiFi toggle switch on the front of the laptop switched on?
On my old laptop I have to switch it on and off a couple of times before my wireless card starts to work.

---

### Post by stephafrain on 2011-09-14
The out put I got was

"07:00.0  Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
              Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
 09:00.0  Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI
 Express Fast Ethernet controller (rev 05)
              Subsystem: Toshiba America Info Systems Device fdc0
              Kernal driver in use: r8169
              Kernal modules: r8169"

That is what I have gotten from said command.

And yes I have flipped my wireless "switch" on and off a couple times. Mine isn't a switch though. It's the "Hold FN press F8 and release" type deal. But yes it's on. It doesn't seem to want to turn off anymore though. the indicator led is at a constant orange/red color.

---

### Post by garvinrick4 on 2011-09-14
This is a fix that has worked for quite a few.

```
sudo add-apt-repository ppa:lexical/hwe-wireless
``` ```
sudo apt-get update
``` ```
sudo apt-get install rtl8192ce-dkms
```
```
sudo reboot
```

---

### Post by stephafrain on 2011-09-14
Great! It is working just fine now. I connect with no problems. :)
Thank you very much for helping me out, I am very happy with my fixed results.
I think I'll now take a look around and make some other posts around the forum.

Cheers mates!

---

### Post by garvinrick4 on 2011-09-14
> Thank you very much for helping me out, I am very happy with my fixed results. You are welcome stephafrain, now if you can go up to thread tools in upper right
and mark as Solved so others with same can benefit.

---

