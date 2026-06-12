---
title: "Broadcom 4313 on lenovo b560"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by riso325 on 2011-06-19
Hi. After reinstalling 11.04 i cant get the wifi work again. The first time i installed 11.04 i got wifi to work but now i dont know hot to. i think there is a conflict as you can see here:


```
administrator@Lenovo-B560:~$ rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

thanks guys for your help :)

---

### Post by westie457 on 2011-06-19
> **riso325 said:**
> Hi. After reinstalling 11.04 i cant get the wifi work again. The first time i installed 11.04 i got wifi to work but now i dont know hot to. i think there is a conflict as you can see here:


```
administrator@Lenovo-B560:~$ rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

thanks guys for your help :)

Hi This should help you

[http://ubuntuforums.org/showthread.php?t=1604868&page=24]("http://ubuntuforums.org/showthread.php?t=1604868&page=24")

If it does not come back here and we will try something different

---

### Post by riso325 on 2011-06-19
ive got a specific broadcom chip 14e4:1427, which is not supported by b43 drivers, can use STA only...

---

### Post by westie457 on 2011-06-19
> **riso325 said:**
> ive got a specific broadcom chip 14e4:1427, which is not supported by b43 drivers, can use STA only...

In a terminal what is the output of

```
lspci -vnn | grep 14e4
```

---

### Post by riso325 on 2011-06-19
here it is...
> 04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0510]

---

### Post by westie457 on 2011-06-19
Open Synaptic and Search for bcm. do not use 'quick search' use the one to the right.
This will show all packages with 'bcm' in them. At the moment we only want the ones that are installed - a green filled box. What are they please. There should only be 3 or 4.

---

### Post by riso325 on 2011-06-19
bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3) and libklibc (i dont think that this one is important)

---

### Post by westie457 on 2011-06-19
You are right, the libklibc is not important.

Now to the (hopefully) solution.

Plug your ethernet cable in if not done already.

In 'Synaptic' Mark for complete removal the 'bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3)' package. Click apply.

If you are told to reboot do not. It is too early.

Next mark 'broadcom-sta-common' and 'broadcom-sta-source'. Click apply.

Now you can reboot and you should be good to go on the wifi.

---

### Post by riso325 on 2011-06-19
no nothing..this was what i tried before (before i reinstalled 11.04) to install older driver but it didnt work to and it doesnt work now :)...when i typed rfkill list before reinstallation the output was:

> 0: ideapad_wlan: Wireless LAN
Soft blocked: yes
Hard blocked: no
1: ideapad_bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no
2: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: no

now there is plus some acer-wifi

---

### Post by westie457 on 2011-06-19
> **riso325 said:**
> no nothing..this was what i tried before (before i reinstalled 11.04) to install older driver but it didnt work to and it doesnt work now :)...when i typed rfkill list before reinstallation the output was:



now there is plus some acer-wifi

Okay I got something slightly wrong here, Try reinstalling 'bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3)' leaving the other packages installed. And reboot again. We are getting there one-step at a time.

---

### Post by riso325 on 2011-06-19
even worse...now the option for enabling wifi in network manager is greyed out :)

---

### Post by westie457 on 2011-06-19
> **riso325 said:**
> even worse...now the option for enabling wifi in network manager is greyed out :)

Oops! That was not supposed to happen.

Now we have established that 'bcmwl' package goofs up it is time to remove it completely. This time do not reboot and try adding b43-fwcutter. Reboot once again. The 'bcmwl' package is the cause of the reboots as it is writing to the kernel I think.

---

### Post by riso325 on 2011-06-19
my chip is not supported by b43: 

[http://wireless.kernel.org/en/users/Drivers/b43#Unsupported_chips](http://wireless.kernel.org/en/users/Drivers/b43#Unsupported_chips)

---

### Post by riso325 on 2011-06-19
before reinstallation wl was working properly...dont know what it is...

---

### Post by westie457 on 2011-06-19
> **riso325 said:**
> before reinstallation wl was working properly...dont know what it is...

I feel stupid now. Have done some Googling and found this

[http://ubuntuforums.org/showthread.php?t=1645143]("http://ubuntuforums.org/showthread.php?t=1645143")

It would appear that you need to use ndiswrapper with the STA driver.
Just checking on what the steps are

It looks like you are going to download a .INF file from either the Lenovo support site or from Broadcom. However you are going to have to boot into Windows to find the exact Driver you need.

In Natty install 'ndisgtk' using 'Ubuntu Software Centre'. Then copy and paste the .INF file to somewhere easy to find eg your home folder.

Run ndisgtk finding it in System Settings (the power-button icon) > System > Windows Wireless Drivers.

This is a step-by step GUI application.

---

### Post by riso325 on 2011-06-19
i found a page : [http://www.stchman.com/install_ndis_broadcom.html](http://www.stchman.com/install_ndis_broadcom.html)
but when i install the inf file the windows wireless driver there is this : 
```
Hardware present: NO
```

---

### Post by westie457 on 2011-06-19
> **riso325 said:**
> i found a page : [http://www.stchman.com/install_ndis_broadcom.html](http://www.stchman.com/install_ndis_broadcom.html)
but when i install the inf file the windows wireless driver there is this : 
```
Hardware present: NO
```

I know this is probably a daft question. Did you follow the instructions on the web-site?

How old is your laptop? and are you dual-booting with a Windows OS?

If running Windows which version?

If the laptop is quite old the correct Driver will have to come from the IBM/Lenovo Support site.
On the site is a tool that will auto-detect your computer and let you know your support options.

---

### Post by superduperlinuxperson on 2011-06-19
your firmware is not the problem; if you look at the first post, it says hard blocked yes, all you need to do is this:
rfkill unblock all
in terminal
thanks

---

### Post by superduperlinuxperson on 2011-06-19
oh and to fix the greyed out enable wireless option run this
sudo NetworkManager
it will tell you its pid, then write this (replace pid with what it told you)
kill pid
sudo NetworkManager

---

### Post by westie457 on 2011-06-19
> **superduperlinuxperson said:**
> oh and to fix the greyed out enable wireless option run this
sudo NetworkManager
it will tell you its pid, then write this (replace pid with what it told you)
kill pid
sudo NetworkManager

     @ superduperlinuxperson

Thank You for saving me a lot of brain-scratching and hair-pulling-out. I don't have enough as it is to do that and as for gnashing of teeth. Don't even go there.

After my last suggestion the next option for me was using the terminal. I would have got as far as ```
rfkill unblock
```

But would have had no idea about sudo NetworkManager```

```

Thanks again and I have learned something new today. That is to read posts properly. You may laugh at me now if you want to.

---

### Post by superduperlinuxperson on 2011-06-19
thats right, im laughing my head all the way to the moon :)

---

### Post by riso325 on 2011-06-20
did not help. ive got a new nb, lenovo b560 i380m etc...dual boot - win7 and ubuntu..in windows everythings ok....after rfkill unbloack all : 


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by superduperlinuxperson on 2011-06-20
acer-wireless is still blocked, so try this:
rfkill unblock 2

---

### Post by riso325 on 2011-06-23
nothing

---

### Post by westie457 on 2011-06-23
Hi what is the output of```
rfkill unblock wifi or rfkill unblock wlan
```

---

### Post by westie457 on 2011-06-23
> **riso325 said:**
> nothing

Forgot to ask. Was that 'nothing' as in the command went straight to the cursor with no output? or was does it mean you still have no wifi?

---

### Post by superduperlinuxperson on 2011-06-24
can you list thhe uotput of:
rfkill list all

---

### Post by riso325 on 2011-06-26
```
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```


westie: there was no output

---

### Post by josephmills on 2011-06-26
could we please see a ```
lsmod 
``` also could I see a ```
sudo lshw -c network 
``` thanks there will be more to come the 4727 is a pain to get the wl to load it gets confused with the open source bcm802 driver or what ever it is called but we will get you up and running. also you have a ethernet cord and internet that way right ?

---

