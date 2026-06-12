---
title: "Sierra Wireless 598 Will Not Attach to ttyUSB"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by wblogan on 2009-03-30
Following the instructions in the  Sprint_Mobile_broadband_Setup_Guide_for_Linux.pdf which I obtained from the Sprint site I am attempting to get a Sierra Wireless 598 to work on a Toshiba Satellite i686 running Hardy 8.04 2.6.24-26-generic. The correct Sierra drivers and scripts are installed. 

However, when I give the "**#sudo modprobe -r usbserial**" it returns "FATAL: Module usbserial is in use" whether the card is inserted in the usb slot or not. None-the-less I run "**#sudo modprobe usbserial vendor=1199 product=0025**". But when I do "**#sudo dmesg|grep -i ttyUSB**" it returns to the prompt.

The logs indicate that the system recognizes the mass storage device which is a part of the card, but it will not attach to ttyUSB, even if I eject or unmount the mass storage device.

I posted earlier when I was attempting to get the Compass 597 working on my Dell; it would attach to ttyUSB but when I dialed I kept getting "no carrier". So I gave up and took the card back to Sprint and got the 598. I had it working before I left the Sprint store parking lot. But I'm having no luck with the Toshiba.

I've searched the web on this 'til I'm sick of it. Can anyone educate me on this? Thanks.

---

### Post by CRCarl on 2009-04-22
I really, really hope you got this solved already, but if not - 

You need to modify your /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi file. 

```
sudo vim /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```

find the section starting on line 220
> 
 <!-- Sierra Wireless -->
      <match key="@info.parent:usb.vendor_id" int="0x1199">
        <!-- EM5625,2x MC5720,2x MC5725,AirCard 595,AirCard 597E,USB Dongle 595U,AirCard 580, Compass 597 -->
        <match key="@info.parent:usb.product_id" int_outof="0x0017;0x0018;0x0218;0x0020;0x0220;0x0019;0x0021;0x0120;0x0112;0x0023;**[B]*0x0025***[/B]">
          <match key="@info.parent:usb.interface.number" int="0">
            <match key="serial.port" int="0">
              <append key="modem.command_sets" type="strlist">IS-707-A</append>
            </match>
          </match>
        </match>

Add the product_id 0x0025 as above. Save the file, exit. Remove the modem, re-insert. Should do it!

Craig

---

### Post by wblogan on 2009-04-22
I'll try your recommendation. I gave the Toshiba to my daughter and son-in-law when I replaced it with my Dell. We got them connected with a Zoom modem which they already had. But I'd still like to get the Sierra Wireless 598 to work on it.

Thanks for your time.

---

### Post by monkey314159 on 2009-05-18
I'm having the same problem as the OP, except when I check .fdi file you mentioned my product ID is located there (0x0120).  
I went here [http://www.nextel.com/en/software_downloads/mobile_broadband/sierra_aircard_595u.shtml](http://www.nextel.com/en/software_downloads/mobile_broadband/sierra_aircard_595u.shtml) and followed the steps.  I'm running ubuntu 8.1 on a PS3 so the only way to use a keyboard and mouse is through USB.  I thought I could be clever and write a script so that it would sleep for 2 minutes (I would then unplug my mouse and keyboard) and then the "modprobe -r usbserial" command would execute, but it still says usbserial is in use.  But if I ignore that and continue on everything seems to work fine.  Then I hit a wall... when asked to ping a website, I get unknown host (or something like that).

I have also tried this much scarier guide. 
[http://www.pbandjelly.org/2006/12/sierra-wireless-aircard-595-configuration-sprintpcs/](http://www.pbandjelly.org/2006/12/sierra-wireless-aircard-595-configuration-sprintpcs/)
But I run into a problem when I tried the "pon sprint"
I got "in file /etc/ppp/peers/sprint: unrecognized option /dev/USB0"

Again, I'm running this on my PS3, dunno if that means anything.  Any suggestions/disparaging remarks about my mother's hygiene would be appreciated.

PS.  I'm new to linux

---

### Post by Ariccanfly on 2009-08-13
> **CRCarl said:**
> I really, really hope you got this solved already, but if not - 

You need to modify your /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi file. 

```
sudo vim /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```

find the section starting on line 220


Add the product_id 0x0025 as above. Save the file, exit. Remove the modem, re-insert. Should do it!

Craig


I also had to download a stupid program from sierrawireless.com/support
and run it in win or mac to "register my modem" or something.

and it claims to support linux on the box! I have more problems with products that claim to run linux than products that claim no such thing.
 
Leave everything in the hands of the manufactures developers and get fubar'ed --so sad. I can think of some video cards with these sorts of problems.

Im starting to understand why windows is so crappy.

Anyways I'm using it now to post this.

An afterthought for the google spiders.

telus mobility 3g scam : they asked me what plan I wanted, when the first two months are unlimited! 

But he doesn't tell me that until after i pay for the 30$ plan.

That really left a bad taste in my mouth.

---

