---
title: "Yet Another LIRC issue"
date: 2009-04-24
forum: Mythbuntu
---

### Post by elgordo123 on 2009-04-24
Hey All, hoping someone can help me out, I'll try to be detailed.. 

Hardware: 
2 PVR-250's
1 Serial IRBlaster from irblaster.info 
Only 1 serial port on Motherboard 

Did fresh install of 9.04 and select "Hauppauge TV Card" for my PVR250 remote my remote works great.   Then I select Serial(UART) : Dish as blaster, blaster doesn't work and remote stops working.   
I've tried everything I can find to no avail, the closest I could get was to have my remote work, and irsend -d /dev/lircd1 SEND_ONCE dish select would give "hardware doesnt support sending" 

Here are my other steps: 
-Followed instructions in PDF Manual for 2 LIRC devices (section 12.2.1)
  /etc/modprobe.d/lirc-serial.conf to: (reboot after each change) 
  options lirc_serial irq=4 io=0x3f8  also tried 
  options lirc\_serial irq=4 io=0x3f8 also tried 
  options lirc \_serial irq=4 io=0x3f8 all with and without softcarrier=1
-Ran setserial, set to manual and modified and copied so that 
  /etc/serial.conf just has /dev/ttyS0 uart none 
-Referred to Don Giovanni's post: [http://ubuntuforums.org/showthread.php?t=789608&highlight=ir+blaster](http://ubuntuforums.org/showthread.php?t=789608&highlight=ir+blaster)
  and also did the 6th post down to switch the order of the include statements in /etc/lircd.conf 
-After that reboot I was able to get haup. remote to work, but still no irblaster (still hardware doesn't support sending) 
-Also tried to run irsend as su and regular user and also sudo chmod a+rw /dev/lircd1 (and all the other /dev/lirc* too) 
-I also dmesg | grep ttyS0 gives: 
[    1.878871] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.879257] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

Did 2nd install and instead of selecting Remote, just select Serial(UART) : Dish for blaster.  Blaster works great, but when I select Haup. remote, both do not work.    So I know both work independently, not together, for now I'm living with just my irblaster and using a k/b for menu's. 

-I should have written this down before, but I also did steps from IR blaster step by step post: [http://ubuntuforums.org/showthread.php?t=616476](http://ubuntuforums.org/showthread.php?t=616476)
but I just ran it (after my 2nd install just above) and when I activate the haup. remote I get this: 
dmesg | grep lirc
[   13.162472] lirc_dev: IR Remote Control driver registered, major 61
[   13.676042] lirc_serial: auto-detected active high receiver
[   13.676050] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 6411.846420] lirc_dev: IR Remote Control driver registered, major 61
[ 6412.086827] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
[ 6412.086860] lirc_dev: lirc_register_plugin: sample_rate: 10
[ 6412.095156] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
[ 6412.095214] lirc_dev: lirc_register_plugin: sample_rate: 10
[ 6412.616037] lirc_serial: auto-detected active high receiver
[ 6412.616046] lirc_dev: lirc_register_plugin: sample_rate: 0

(It may have been different when I was doing all the steps above, before my 2nd install).   


-Both my remote and blaster work independently, but I can't get them to work together :(    

  
Thanks for the help!

[SOLVED] View this thread on using knoppmyth's irblaster script:
[http://ubuntuforums.org/showthread.php?p=7145522#post7145522](http://ubuntuforums.org/showthread.php?p=7145522#post7145522)

---

