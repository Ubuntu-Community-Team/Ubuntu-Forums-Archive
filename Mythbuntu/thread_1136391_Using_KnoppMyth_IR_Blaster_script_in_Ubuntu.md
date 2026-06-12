---
title: "Using KnoppMyth IR Blaster script in Ubuntu"
date: 2009-04-25
forum: Mythbuntu
---

### Post by whiteright on 2009-04-25
One thing that's better about KnoppMyth than the other MythTV distros is the ir blaster setup. You just have to run a script and you're up and running. I've been using MythBuntu since about 7.10 but I've never been able to get the built-in ir blaster setup going, so I've ended up just copying the script files from KnoppMyth. I'd never documented this, but I had to rebuild my box with Jaunty and I wrote it down as I did it. Here are the steps:

1. Download KnoppMyth R5.5. Mount the iso using the following commands:
    sudo mkdir /media/knoppmyth
    root@mythtv:/home/michael# mount -o loop KnoppMythR5.5.iso  /media/knoppmyth/

2. Install cloop-utils and dialog package using apt-get
3. Extract the KnoppMyth files using "extract_compressed_fs /media/knoppmyth/KNOPPIX/KNOPPIX > knoppmythfiles"
4. Mount the KnoppMyth image using "sudo mount -o loop knoppmythfiles /media/knoppmythfiles"
5. Run the following copy commands to copy the files from KnoppMyth CD:

    cp /media/knoppmythfiles/usr/local/bin/irblaster.sh /usr/local/bin
    mkdir /usr/local/share/knoppmyth
    cp -r /media/knoppmythfiles/usr/local/share/knoppmyth/irblaster /usr/local/share/knoppmyth
    cp /media/knoppmythfiles/etc/init.d/irblaster /etc/init.d
    cp /media/knoppmythfiles/usr/local/bin/knoppmyth_functions.bash /usr/local/bin

6. Run the irblaster.sh script and follow the prompts. 
7. Set the channel change script in mythtv-setup to /etc/irblaster/channel_change.sh
8. Remove the file /etc/modprobe.d/KnoppMyth. 

This sounds like a lengthy process with downloading an iso - but I found that it was up within ten minutes of getting the iso, against weeks spent trying to get the ir blaster going in other ways.

---

### Post by elgordo123 on 2009-04-25
I too am having problems with it (my post down the list).  I have a PVR-250 remote and a serial IRBlaster.  Do you know if this will work in my configuration?

---

### Post by whiteright on 2009-04-25
It's always worked for me. The only thing you might have to do is download an lircd.conf file for your set top box if it isn't in the list of those supported by the script. The script asks you to choose your set top box from a list. Some of the options can be used for other boxes. I chose Sky Digibox, to control foxtel in Australia. I'm using a PVR-500, a serial ir blaster, and a StreamZap remote. I would give it a go.

---

### Post by syphr42 on 2009-04-25
I have been doing the same thing since I switched from Knoppmyth to Mythbuntu back with 7.10. I didn't really need everything in the Knoppmyth script, so I just grabbed the relevant parts for my situation, but I spent days trying to get LIRC working on Mythbuntu as both a transmitter and a receiver with no luck (it works fine for me out of the box as just a receiver) and the script from Knoppmyth worked like a charm.

---

### Post by elgordo123 on 2009-04-25
That did the trick!  I unselected the irblaster and remote, then rebooted.  I then just selected my PVR-250's remote (Hauppauge TV Card) and made sure it worked.  
I then followed your instructions and it works perfectly.   I took a little extra time and made an installer (and Readme file!) so that it will be easier for future users.  
Just tar zxvf blasterinstall.gz in your /home/(user) directory on your mythbuntu box, cd blasterinstall, view the readme and install. 

:guitar:

---

### Post by tegwilym on 2009-04-29
So all this works with a serial IRblaster?  I'm currently running Mythdora 5 on my machine, and would like to try MythBuntu, but in the past the IRblaster has just given me fits.  I did get it working in Mythdora ok (after a lot of work!), but really want to try this one. 
I have mine shooting at an older RCA DirecTV box.  RCA 770 I think was what I'm using for the Lirc codes. 

Tom

---

### Post by KermitJr on 2009-10-10
Thank you for taking the time to document this. I hope the mythbuntu people are paying attention!

---

