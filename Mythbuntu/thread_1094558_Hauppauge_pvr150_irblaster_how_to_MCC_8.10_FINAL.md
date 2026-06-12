---
title: "Hauppauge pvr150 irblaster how to MCC 8.10 FINAL"
date: 2009-03-12
forum: Mythbuntu
---

### Post by scooter29 on 2009-03-12
Mythbuntu 8.10 **_PVR150 irblaster will not work out of the box._** Using MCC all I could get working was the remote, even if I cut and pasted the /etc/lirc/lirc.conf file listing the blaster first.

I had to completely remove lirc to get this to work. Make backups of /etc/lirc/lircd.conf and hardware.conf FIRST! at least hardware.conf for sure!

from command line (terminal)

[FONT="Courier New"]sudo cp /etc/lirc/lircd.conf /etc/lirc/lircd.conf.bak
sudo cp /etc/lirc/hardware.conf /etc/lirc/hardware.conf.bak
sudo apt-get --purge remove lirc[/FONT]

This will also uninstall mythbuntu Control Centre - mythbuntu-lirc-generator as well! Don't fret as when you're done just reinstall with synaptic package manager.

Then follow Marks directions. 
[http://www.blushingpenguin.com/mark/blog/?p=24]("http://www.blushingpenguin.com/mark/blog/?p=24")


Don't do his commands together or that have the && sign combining them. break them up. For example Just do a 
[FONT="Courier New"]sudo make[/FONT] (then)
[FONT="Courier New"]sudo make install[/FONT]
and
[FONT="Courier New"]sudo modprobe lirc_dev debug=1[/FONT]. When finished do a 
[FONT="Courier New"]sudo modprobe lirc_pvr150 debug=1[/FONT].

You will need the firmware saved under /lib/firmware and Mythbuntu's lircd.conf files _**DO NOT WORK!!!**_ Follow Mark's directions on creating your own, putting the irblaster before the remote (in your custom cofig file) and saving as /etc/lirc/lircd.conf 

Edit your hardware.conf ( /etc/lirc/hardware.conf ) file listing only "lirc_dev lirc_pvr150" in the modules selection of remote and "/etc/lirc/lircd.conf" as your location everything else left blank or "" in both remote and blaster sections. 

I googled and found a shell script for my change channel.sh as I had problems with perl. I also had to modify script as my reciever on Mark's site did not list a select button. I had to replace power in the script instead of select. This allows my reciever to wake up from press select to watch tv screen. Mythbuntu needs 
[FONT="Courier New"]irsend -d /dev/lircd[/FONT]
to work correctly.

Don't forget to change authorities of your script!
[FONT="Courier New"]sudo chmod +x nameofscript.sh[/FONT]

You should be able to irsend from command line, just remember that mythbuntu loads your blaster as /dev/lircd not /dev/lirc0 ( after reboot, or you can just modify Marks command when he loads device, so as to not confuse you with your script ) 

Change
lircd --device=/dev/lirc0 to
[FONT="Courier New"]sudo lircd --device=/dev/lircd[/FONT]  

I should also tell you that I looked at the mythbuntu installation guide under LIRC 12.21 serial ir transmitter, and I had to create a file under /etc/modprobe.d/lirc
[http://www.mythbuntu.org/documentation/mythbuntu_8.10_installation.pdf]("http://www.mythbuntu.org/documentation/mythbuntu_8.10_installation.pdf")

reconfigured lirc-serial

[FONT="Courier New"]sudo dpkg-reconfigure setserial[/FONT]

selected manual and added text ( /dev/ttyS0 uart none ) to /var/lib/setserial/autoserial.conf and then saved and copied that file in /etc/serial.conf folder as well.

[FONT="Courier New"]sudo cp /var/lib/setserial/autoserial.conf /etc/serial.co[/FONT]nf

Then I went to synaptic package manager searched for Mythbuntu Control Centre and selected to reinstall. When it loads it will try and overwrite your lircd.conf file and hardware.conf file just select keep your own. 

Open up MCC and select ir devices, select custom for remote, your config is /etc/lirc/lircd.conf, check to make buttons. **_DO NOT SELECT A IR DEVICE._** 
Reboot, if you hit Ctrl,F1 when your splash screen loads it looks like lirc fails, however if your lircd.conf file is set correctly it should work. 

All of this together should get you going. 
GOOD LUCK!:popcorn:

---

### Post by scooter29 on 2009-04-01
Did this not at least help one person? I struggled without this for several weeks, now detailed directions, and not one comment?! Go Figure.:(

---

### Post by codymyth on 2009-04-02
Ok i followed your and marks advice and i got the remote working(not the ir blaster cause i broke it lol) but i can't not get a tv signal from my pvr150 card, i set up a turner card so i don't know why i am not seeing anything.

---

### Post by codymyth on 2009-04-03
Ok i figured out the image issue

I Do have another issue though. everytime i restart my system my remote stops working. And also i am using S-Video for input so how do i get sound?

---

### Post by scooter29 on 2009-04-09
If you broke your blaster, you do not need Mark's driver. Just setup your remote using Mythbuntu Control Centre, only select remote not the blaster option, it should work. As for your sound issue you will need a mini jack to stereo rca splitter and stereo rca cables from your source into hauppauge card and stereo rca cables from your sound card to tv, as svideo does not carry sound only picture. I was looking at purchasing a better blaster anyway as the signal from pvr150 is really weak. Iguana works makes an excellent one and has tech support.
[http://iguanaworks.net/products.psp]("http://iguanaworks.net/products.psp")
Good Luck!

---

