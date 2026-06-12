---
title: "wpa2 wireless"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by c00lwaterz on 2010-03-26
hi,

In my toshiba m900 with realtek wireless lan. i canot detect any network. should i see any network? i setup my access point using wpa2 in windows.

need help. how about the ubuntu 10.04? i mean do they support wpa2 and wireless issues?

---

### Post by chili555 on 2010-03-26
You should see networks if your network card has a driver and has created an interface. Please open Applications > Accessories > Terminal and type:```
iwconfig
```Do you have a wireless interface, wlan0 perhaps? If not, we'll need to do some more troubleshooting. If you do have an interface, try:```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Substitute your interface if it is not wlan0.

Now do you see networks?

Ubuntu supports WPA2 very well. I am posting using it right now.

---

### Post by c00lwaterz on 2010-03-26
when i type iwconfig, it says no wireless extensions

---

### Post by chili555 on 2010-03-26
It appears that you do not yet have a driver associated with your card. I am assuming it's an internal card. Please post:```
lspci -nn
```If it's a USB device, please post:```
lsusb
```Thanks.

---

### Post by c00lwaterz on 2010-03-26
i tried to get the driver in windows then i saw it's present but the ndiswrapper cannot setup. im checking the networking tool but no wireless option. I go to wireless device but the driver cannot edit settings.

I also have high temperature using ubuntu. really hot. im not kidding. im afraid it might fry up my laptop. why causing so much heat?

I have follow this guide but no luck. my wired connection is working but after following this guide ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) then my wired got problem also. wireless have no luck until now. =(

---

### Post by chili555 on 2010-03-26
Please run:```
top
```Are any processes using a lot of CPU cycles? Any process you can kill?```
sudo killall whatever
```Please see attached.

---

### Post by c00lwaterz on 2010-03-26
i just use the firefox for ubuntu help and the terminal window for typing command. but really hot

---

### Post by chili555 on 2010-03-26
> **c00lwaterz said:**
> i just use the firefox for ubuntu help and the terminal window for typing command. but really hotI don't understand your answer. Did you run *top*? Were there any runaway processes? Did you kill them?

---

### Post by c00lwaterz on 2010-03-26
i also try to uninstall ubuntu then install again but same (so hot and wireless prob) but i think i'm more afraid of being hot. maybe it will burn =(

---

### Post by c00lwaterz on 2010-03-26
now I will reinstall again to gain back my wired internet so i can view forum

---

### Post by c00lwaterz on 2010-03-26
im now in ubuntu. using wired connection. fresh install ubuntu 9.1. running firefox and terminal only. not yet hot., maybe after 1 minute it will get hot then i will run the top.

I run lspci -nn

the result is 

2:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
02:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
08:00.0 VGA compatible controller [0300]: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series] [1002:9553]
08:00.1 Audio device [0403]: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series] [1002:aa38]

---

### Post by chili555 on 2010-03-26
> Realtek Semiconductor Co., Ltd. Device [[COLOR="Blue"]10ec:8172[/COLOR]] (rev 10)

It is supposed to work with the module *r8192se_pci*. I suggest the live CD for 10.04 to see if it does. The other alternative is a download and compile from Realtek's site. Which do you prefer?

Wow, that was a fast re-install!

---

### Post by c00lwaterz on 2010-03-26
do i need to download the 10.04? if i will download it may take hours. =) it will fix the wireless?

p.s. I guess that the one overheating is my ati radeon. because now its not installed because when i install the ubuntu i did not put internet on wired. so it is not install automatic. now its not hot. so  guess its my video card ati radeon 4500

---

### Post by chili555 on 2010-03-26
We don't know, but I think so. The driver is built-in:> /lib/modules/2.6.32-16-generic/kernel/drivers/staging/rtl8192e/r8192_pci.ko
/lib/modules/2.6.32-16-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
/lib/modules/2.6.32-16-generic/kernel/ubuntu/rtl8192se/r8192se_pci.koThe alternative is a lengthy compile. Search this forum for r8192se.

---

### Post by c00lwaterz on 2010-03-26
i tried to search here in forum the r8192se but no result

---

### Post by chili555 on 2010-03-26
[http://ubuntuforums.org/showpost.php?p=8335065&postcount=2](http://ubuntuforums.org/showpost.php?p=8335065&postcount=2)

---

### Post by c00lwaterz on 2010-03-26
thanks, now im following the instructrions in your thread =)

---

### Post by c00lwaterz on 2010-03-26
i follow all then the result is

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


i see in network the network available but i tried to connect and type the wpa2 password but cannot connect to access point. how to check if im connected?

thanks =)

---

### Post by chili555 on 2010-03-26
Please do:```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 power on rate auto
```Now try to connect and see if you have better success.

---

### Post by c00lwaterz on 2010-03-26
when i try to connect to my accesspoint it says, wireless disconnected. =(

---

### Post by chili555 on 2010-03-26
With the ethernet disconnected?

---

### Post by c00lwaterz on 2010-03-26
im in wired while connecting to my access point. then it says wireless disconnected. i will try to disconnect in wired.

---

### Post by c00lwaterz on 2010-03-26
i still cannot connect. it says disconnected wireless network.

I want to add this. its now starting to become hot. =( i dont know why. hoping to be fix in lucid if lucid is the only hope =( im really sad 4 years already with ubuntu but i cant go dive on ubuntu only. i can use ubuntu with minimum time because of issues. really sad for no luck

---

### Post by chili555 on 2010-03-26
Does *top* show any runaway processes?

---

### Post by c00lwaterz on 2010-03-27
below I attahed the top print screen.
I also notice my open office word processor is not working
i saw some cpu% 40 to 50 and memory 30 to 60.

wireless still don't connect. but now i can see the accesspoint and other wireless network. it just don't connect even i put the pass key.

---

### Post by c00lwaterz on 2010-03-27
I have to uninstall the ubuntu.

reason is:

after trying to fix wireless then i try to shutdown and to reboot.
It was really hot then. after pushing the button "on" in my laptop, it won't start. It really won't start even in the bios. I keep pressing the button. then I try to put my laptop near the aircon to cool off. then when i press the button "on" suddenly it start. maybe its really hot so it cant turn "on"

is there any other distros can i try? I want gnome, I also want compiz. my videocard is ati radeon 4500. I want easy to use as ubuntu. I prefer to use the ubuntu than fedora ( the menu). Im comfortable with the style of ubuntu to find the programs and look and feel. any recommendation?

thanks

---

### Post by chili555 on 2010-03-27
This is evidently a known issue with some Toshiba laptops: [http://ubuntuforums.org/showthread.php?t=1282161](http://ubuntuforums.org/showthread.php?t=1282161)

I am certain that it is an issue with ACPI and the way the Linux kernel implements it. I am not at all sure that it is relate to Ubuntu specifically, but rather the kernel.

It doesn't even seem to be limited to Linux: [http://laptopforums.toshiba.com/t5/General-Technology/Satellite-E105-S1402-Running-Hotter-After-ACPI-Flash-BIOS/m-p/33039](http://laptopforums.toshiba.com/t5/General-Technology/Satellite-E105-S1402-Running-Hotter-After-ACPI-Flash-BIOS/m-p/33039)

[http://forums.techguy.org/windows-xp/585088-solved-toshiba-laptop-windows-xp.html](http://forums.techguy.org/windows-xp/585088-solved-toshiba-laptop-windows-xp.html)

I am sorry I could not have been of more help.

---

### Post by c00lwaterz on 2010-03-27
you are a big help. by replies you made, its a big help to me.. thanks. I want to add you in my friend list here in ubuntu forum. I know you are a big help for me. 

I appreciate every steps and guide you teach me.

if there is solution with the temperature then that is great. its hard to fix other problem while high temperature. really hot in my palm hehe.

for now i use windows vista. other people recommmend fedora. but i read fedora. i think they have same issue also with toshiba. i mean the heat issue. because i read wireless and graphics issue same as ubuntu and linux mint. they are fixing it right now for fedora 13 and same as lucid. maybe i need to wait. I will not give up on linux. I will try and try.

pls add me to your contact. thanks =)

---

### Post by chili555 on 2010-03-27
> pls add me to your contact. thanks =) I have done so, thank you. Thank you for your kind comments. I hope there will be a solution and that you will be back soon.

---

### Post by c00lwaterz on 2010-03-27
I will keep an eye here in forum.  Im waiting for the lucid to be release. maybe they try fixing some issues regarding toshiba.
im hoping hehe

sorry for my bad english. =)

---

### Post by c00lwaterz on 2010-04-09
hi chili555,

I can't message you in visitors message because I don't have much beans. it says I need 75.

so here is my message:

Hi Chili555,

I have downloaded ubuntu 10.04 beta2 and test it on virtual box. My issue in karmic is wireless and High temp. But i want to fix first the high temp. I want to let you see the testing I have done. How to give you my screen shot? on the left there of the picture is widget that monitor my cores and the temperature. Lets discuss this. You want to create new thread? or where should I post? =)

I know you are the one can help me.

Thanks a lot and in Advance =)

so here is the attachment and the message :lolflag:

thanks

---

### Post by chili555 on 2010-04-09
I think your question is better asked in General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331) or else Lucid Lynx Testing and Discussion: [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

If I read your widget correctly, and it's pretty tiny for my old eyes, your processors are running at 60 degrees C. I don't think that's terribly hot; my laptop is running now at 58 degrees C.

This is an area outside my experience. Sorry I can't be of more help.

---

### Post by c00lwaterz on 2010-04-09
hi chili555,

I have run the ubuntu 10.04 on virutalbox using windows vista OS. then in my windows widget the temperature is 60 degrees C.

My question is: if I use ubuntu 10.04 in virtual box is it running same in livecd boot (I mean the temperature)?

also if the 60 degrees C is ok in laptop? i mean is it not bad? or bad? example if my laptop reach 75 degrees c., is it bad already?

thanks =)

---

### Post by chili555 on 2010-04-09
Please see my post above, especially:> I think your question is better asked in General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)  or else Lucid Lynx Testing and Discussion: [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by c00lwaterz on 2010-04-09
yes I have tried.

maybe I should do it myself to fix my issues regarding temp..

thanks thanks

---

