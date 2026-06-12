---
title: "Aireplay-ng: cannot false authenticate"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by dbzkid on 2010-05-13
I'm on ubuntu 10.4 and Cant seem to falsely authenticate myself with my AP. I am trying to break a wep key on one of my older linksys routers; It continues to say this:

```
root@kevin-laptop:/home/kevin# aireplay-ng -1 1 -a xx:xx:xx:xx:xx:xx mon1
No source MAC (-h) specified. Using the device MAC (xx:xx:xx:xx:xx:xx)
11:39:16  Waiting for beacon frame (BSSID: xx:xx:xx:xx:xx:xx) on channel 6

11:39:16  Sending Authentication Request (Open System) [ACK]

11:39:18  Sending Authentication Request (Open System) [ACK]

11:39:20  Sending Authentication Request (Open System) [ACK]

11:39:22  Sending Authentication Request (Open System) [ACK]

11:39:24  Sending Authentication Request (Open System) [ACK]

11:39:26  Sending Authentication Request (Open System) [ACK]

11:39:28  Sending Authentication Request (Open System) [ACK]

11:39:30  Sending Authentication Request (Open System) [ACK]

11:39:32  Sending Authentication Request (Open System) [ACK]

11:39:34  Sending Authentication Request (Open System) [ACK]

11:39:36  Sending Authentication Request (Open System) [ACK]

11:39:38  Sending Authentication Request (Open System) [ACK]

11:39:40  Sending Authentication Request (Open System) [ACK]

11:39:42  Sending Authentication Request (Open System) [ACK]

11:39:44  Sending Authentication Request (Open System) [ACK]

11:39:46  Sending Authentication Request (Open System) [ACK]
Attack was unsuccessful. Possible reasons:

    * Perhaps MAC address filtering is enabled.
    * Check that the BSSID (-a option) is correct.
    * Try to change the number of packets (-o option).
    * The driver/card doesn't support injection.
    * This attack sometimes fails against some APs.
    * The card is not on the same channel as the AP.
    * You're too far from the AP. Get closer, or lower
      the transmit rate.

root@kevin-laptop:/home/kevin# 

```

I'm using an eeepc 701 it has an Atheros card and does injection. I have also tried it with backrack 4 and it works perfectly (it falsely authenticates with the ap and decrypts the wep key) I just cant seem to get it to work on ubuntu 10.4. Could it be a kernel issue? Has anyone else run into this issue or something similar?

[COLOR="SeaGreen"]**Ok, so I found out that there is a bug in the new(er) kernel(s).**[/COLOR] If you use an older kernel (I used 2.6.31-14 which can be found [here]("http://packages.ubuntu.com/karmic/linux-image-2.6.31-14-generic-pae")) and it magically works. (Thanks hardkorek for the info found [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530449"))

---

### Post by sathishmk0280 on 2010-05-25
hii..buddy..iam also trying the same with ubuntu 10.4 and getting the same error. Thanks for the post. Let me check it and update you and in between if u got it work please post it also

---

### Post by yaywoop on 2010-09-19
fixed this by installing the v2.6.35-rc1-lucid kernel from here
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/)

although then airodump-ng and aireplay-ng where complaining about the card always being in channel -1, which is apparently a bug in ath5k
I fixed that by recompiling [Compat-wireless]("http://wireless.kernel.org/en/users/Download/stable/") with [this patch]("http://patches.aircrack-ng.org/channel-negative-one-maxim.patch") 
in the extracted directory run 
patch ./net/wireless/chan.c ./channel-negative-one-maxim.patch
and follow the rest of the instructions on the compact-wireless download page

---

### Post by soad6 on 2010-10-16
Ok im running the new ubuntu 10.10 with kernel 2.6.35-22. I have no idea how to get that patch to work. I tried it and it gave me 2 out of 2 hunks failed. line 49 and 72. Not sure what to do now, this issue should be fixable with the maxim patch just can some one make a deb file with it to auto install or a script?  Cuz I'm not much good at compiling for scratch.

---

### Post by soad6 on 2010-10-16
Ok im running the new ubuntu 10.10 with kernel 2.6.35-22. I have no idea how to get that patch to work. I tried it and it gave me 2 out of 2 hunks failed. line 49 and 72. Not sure what to do now, this issue should be fixable with the maxim patch just can some one make a deb file with it to auto install or a script?  Cuz I'm not much good at compiling from scratch.

---

### Post by yaywoop on 2010-10-16
Its not too hard to compile, here is how i did it
you may need these depencies:
```
sudo apt-get install build-essential 
sudo apt-get install libssl-dev 
sudo apt-get install openssl-dev 
```
not sure which one of those ssl packages is actually required

so download and extract the latest stable compact-wireless and that patch file.
```
cd compat-wireless-2.6.35-1/
patch ./net/wireless/chan.c ~/Downloads/channel-negative-one-maxim.patch 
./scripts/driver-select ath5k
make
sudo make install
```

---

### Post by soad6 on 2010-10-17
This issue isnt with compat-wireless its a kernel related issue. sorry its in the bugs list and confirmed by 2 people. Also changing the kernel to the previous kernel fixes this problem.

---

### Post by yaywoop on 2010-10-17
this is true updating or reverting the kernel fixes the original problem. I thought you where encountering the same "-1 channel" bug I was encountering after the kernel change, thus needed to patch compact-wireless.

---

### Post by SquirrelScript on 2010-10-17
> **soad6 said:**
> This issue isnt with compat-wireless its a kernel related issue. sorry its in the bugs list and confirmed by 2 people. Also changing the kernel to the previous kernel fixes this problem.
Ive found that it IS a problem with compat-wireless, NOT the kernel!
In: ./scripts/update-initramf
Its been hard coded to use "2.6.31", hence why its works if you downgrade the kernel to this version. 
My solution: [http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)

---

