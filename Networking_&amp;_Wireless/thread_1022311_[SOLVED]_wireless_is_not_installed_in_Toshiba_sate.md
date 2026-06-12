---
title: "[SOLVED] wireless is not installed in Toshiba satellite L300-190"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by mali2 on 2008-12-26
Now I have installed the ubuntu 8.1 , it is working well... in my laptop... but wireless and sound is not working, how can i update that driver, whenever i use the hardware driver ... it says "No proprietary drivers are in use on this system"
please help me out, ur guide is realy very usefull every time.

---

### Post by Jakey_TheSnake on 2008-12-26
For wireless: 



Download this wireless driver: [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz) 

Move it to your Documents folder and extract. 

Open up a Terminal (Applications > Accessories > Terminal)

Type:

```
cd /home/username/Documents/madwifi-hal-0.10.5.6-r3879-20081204
```

(NB: to make this stage easier. If you press "tab" after the first few letters of "madwifi" it will automatically put in the rest of the folder name for you. Please note that the folder name above is default after extraction).

Press enter. Then type:

```
make
```

Will take a couple of minutes, wait until you get the correct starting prompt again. 

Then type:

```
sudo make install
```

Let it do it's stuff, then:

```
modprobe ath_pci
```

Restart laptop, then when you click your networks icon you should get that beautiful list of wireless networks to connect to. 

Hope this helps, 

- Jake.

When you talk about the driver, I assume you mean sound driver? What's your sound card?

---

### Post by mali2 on 2008-12-27
> **Jakey_TheSnake said:**
> For wireless: 



Download this wireless driver: [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz) 

Move it to your Documents folder and extract. 

Open up a Terminal (Applications > Accessories > Terminal)

Type:

```
cd /home/username/Documents/madwifi-hal-0.10.5.6-r3879-20081204
```

(NB: to make this stage easier. If you press "tab" after the first few letters of "madwifi" it will automatically put in the rest of the folder name for you. Please note that the folder name above is default after extraction).

Press enter. Then type:

```
make
```

Will take a couple of minutes, wait until you get the correct starting prompt again. 

Then type:

```
sudo make install
```

Let it do it's stuff, then:

```
modprobe ath_pci
```

Restart laptop, then when you click your networks icon you should get that beautiful list of wireless networks to connect to. 

Hope this helps, 

- Jake.

When you talk about the driver, I assume you mean sound driver? What's your sound card?

while doing the above thing i got the following error: I am attaching the screen shot of it.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97726&stc=1&d=1230374399[/IMG]

---

### Post by mali2 on 2008-12-27
for overcoming the above problem i tried to login through root, It does not gives an error while executing the last command "modprobe ath_pci" but shows nothing after it... and then i restart my computer but no wireless still same with wired network :(
I m attaching the screen shot.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97727&stc=1&d=1230376254[/IMG]

---

### Post by mali2 on 2008-12-27
still no suggesstion... :(:(:confused:

---

### Post by mali2 on 2008-12-28
Hello any body... any one... please help me out, i m in urgency. :confused::confused::confused:

---

### Post by itexorcist on 2008-12-28
> **mali2 said:**
> Hello any body... any one... please help me out, i m in urgency. :confused::confused::confused:

I am having the same problem ? pleased to see you, I am not alone.   :P

---

### Post by mali2 on 2008-12-28
> **itexorcist said:**
> I am having the same problem ? pleased to see you, I am not alone.   :P

same here... but i m realy worried about my problem, i have lot of work to do in ubuntu, regarding my studiez... and it is realy a big problem for me... have u tried the above solution?, it is not working for me. :confused:

---

### Post by mali2 on 2008-12-28
I have also tried the "lspci" command, but i dont know here which one is my wireless , infact here is no wireless inlisted. I have the screen shot of it below.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97844&stc=1&d=1230481557[/IMG]


any expert suggesstion :confused: ???

---

### Post by mali2 on 2008-12-30
My wireless having this information, i got it from windows vista 
"Realtek RTL8187B Wireless 802.11b/g 54Mbps USB 2.0 Network Adapter"


Still no suggesstion :( ???

---

### Post by mali2 on 2008-12-30
Satellite L300-190 Wireless [RTL8187B - 8198chip] 

--------------------------------------------------------------------------------

Toshiba Satellite L300-190 Wireless
Realtek RTL8187B Wireless 802.11b/g 54Mbps USB 2.0 Network Adapter


1. by using the lsusb i got the following information about my wireless:
"Bus 008 Device 002: ID 0bda:8198 Realtek Semiconductor Corp"

2. Then according to the reference of ubuntu forum i used the steps for manually configuring my wireless 
[https://help.ubuntu.com/community/Wi...ealtekRTL8187b](https://help.ubuntu.com/community/Wi...ealtekRTL8187b) and then to be more specified about my wirless i used the reference below.
[http://www.doc.ic.ac.uk/~pgp/persona...-wifi-old.html](http://www.doc.ic.ac.uk/~pgp/persona...-wifi-old.html)

3. after doing all the steps according to the guide... I used:

....Step 4. patch -p1 < 2.6.24.patch
Step 5. Make changes in the /wifi/rtl8187/r8187_core.c (Search for 2 lines containing "0x8189". Change both to "0x8198" instead...)
Step 6. Now here is the problem... when i used this command sudo ./makedrv. I got two errors,but it is also mention there that "Ignore the swathes of warning messages." so i used to ignore it. but when i come at step 7 there was a big blunder

Step 7: Load the driver using sudo ./wlan0up.
and I got the following problems... while executing step-7:

insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory

and then i also ignore this , and carry on with the next steps, but it did nt work, but i feel the problem is right at step 7, i tried again and again... but still same problem, Now please let me know, where is the problem???

---

### Post by mali2 on 2008-12-31
Fianally Wireless list have got by using the following driver and instructions for the the laptop Toshiba satellite L300-190...
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)
as I am using ubuntu 8.10 , so i installed compact driver supported for 2.6.27. 
and just untar it...
1.make
2. sudo make install
3. sudo make unload
4. sudo make load.
and restart ur PC, and thats all, hopefully for the next start u can see the wireless connections:D:D:D:D. BBBUTTTTT ....:(
For me problem is still there... 
I can connect with my Router but after 2-4 mins succesfully suffering internet, it stops working... and no reply from the internet, and seems like halt... and if i try to connect it again then it do no connect with my router... so... problem still there... and i also tried the bit rate fixed to 5.5 rc.local but still same condition... :confused::confused::confused:

---

