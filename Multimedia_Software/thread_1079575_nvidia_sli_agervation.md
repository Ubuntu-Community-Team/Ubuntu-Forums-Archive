---
title: "nvidia sli agervation"
date: 2009-02-24
forum: Multimedia Software
---

### Post by Homunculi on 2009-02-24
ok 
i am getting a little frustrated ... 
i just got 2 9500gt 1gb cards 

this is the first time i have done a sli with pci-e 

i see in the forums several ppl having trouble with the nvidia driver 
i have tried to get them working but to no avail 

the grep info is :
pci:02:00.0 9500gt nvidia corp 
pci:07:00.0 9500gt nvidia corp 

and i dloaded the latest nvidia driver 180.29
folloed the steps on 4 differnt howto's on here and getting nowhere fast 
i keep getting :
a blank screen 
check battery ... 
or it just boots down to a promp sayng normal boot 

after looking thru the howto's 
i have moded the xorg.conf with:

Busid "PCI:2:0:0"
Driver "nvidia" (with r without this line same result)
Options "sli" "auto"

i have gone thru the steps of purging all the nvidia drivers 
and and added a line in modules common 

i am at a loos here i worked with it for 14 hours now 

here is my system layout 
2 9500gt 1gb 
amd x2 6000+
sb audigy 
2 1gb nvidia nic controlers 
3 sata hdd drives 
2 plextor dvd-dl ide 
1 pioneer dvd-dl sata 
and 3gb ddr800

i was running 7.04 ff with a 7600gt before no problems 
 
seen the op to get a upgrade 
and i upgraded to 8.10 because 7.04 met it's end of life 
if any idea's to get this working i would love to hear it

---

### Post by Homunculi on 2009-02-25
i tried this way last night to no avail !!!! 

Finally I managed to make it work, thanks to all the help i got. 
So to resume everything that one must to make the nvidia drivers work for Linux 
8.10 on a Studio XPS 13: 
 
1.Exit the GUI, type: "Ctrl+Alt+F1" 
( to return press Ctrl+Alt+F7) 
 
2. $ sudo killall gdm 
(to stop the GUI) 
 
3. $ sudo apt-get install nvidia-180 modaliases 
(this will download the driver from internet, and since I'm not sure how to 
connect with wifi, use ethernet) 
 
4. $ sudo apt-get install nvidia-glx-180 
(this will install the driver, just enter y when it is asked) 
 
5. When the install is finished: 
$ sudo nvidia-xconfig 
(there will be an error, doesn't matter) 
Type in the same command again 
(this time it will work) 
 
6. $ sudo reboot 
(restarts the computer) 
 
7.At this point it will give the error, 'no screens' 
enter your username and password then: 
 
$ sudo nano /etc/X11/xorg.conf 
(this will edit the xserver configuration page) 
 
8.Go down to "Section Device" 
And add a the very end the line: 
BusID "PCI:03:00:0" 
(remember this is for the studio xps 13) 
 
9.Quit the editor with: 
Ctrl+X <Enter> 
then: 
Y <Enter> 
then: 
<Enter> 
 
10. reboot the computer once more and tadaaa, it works 
 
I spent such a time to make this work, I was very happy when it finally worked, 
thanks alot for the help from everybody. 
 
P.S If this doesn't work just reboot the computer choose the restricted 
partition, and just do do "Repair X"

---

### Post by Homunculi on 2009-02-25
thank you ,,,, thank you ... 
for every one who replied to this help request 
i got it working ... in sli mode 

i used dogpile on the internet 

again ... thanks for the help :lolflag:

---

### Post by Homunculi on 2009-02-27
ok that was my attempt at 8.10 ... 
i needed to so something in windows ... 
rebooted into intrepid and things were a mess 
it was worse that what a matrox millenia card could do in win95 
... 
no borders  nothiung it was ugly ... 
reloaded 8.04 .. got the sli running in no time flat 
and was able to get things working in an hour vs 6 days if reading a rebooting ... reinstalling 

8.10 is good looking .. just a little unstable for me at the time 

will see how things go later on ;)

other than that i have questions about sli 

i have 2 9500 gt 1gb cards 
got quake 4 to load and looked at the terminal ... only 1gb of video mem was showing avail 
 personally i  have not done a sli since the voodoo 2 cards from 3dfx 
is there a glitch in the driver that is misreporting ? 

but i got 2 cards for the price of 1 .. 

let me know ... thanks

---

