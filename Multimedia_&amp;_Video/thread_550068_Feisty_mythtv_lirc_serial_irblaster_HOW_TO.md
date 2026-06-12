---
title: "Feisty mythtv lirc serial irblaster HOW TO"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by tagra123 on 2007-09-13
HOW TO MYTHTV LIRC SERIAL IRBLASTER 

TIME TO COMPLETE: 10 to 15 minutes (including downloads)

Making lirc work in any version of Ubuntu seems more difficult than necessary.

This has been adapted from another how to located here:

[http://losdos.dyndns.org:8080/public/mythtv-info/MythTV_DISH_IR_LED_TX_via_Modified_LIRC.html?#Note_for_Troubleshooting_LIRC_Make](http://losdos.dyndns.org:8080/public/mythtv-info/MythTV_DISH_IR_LED_TX_via_Modified_LIRC.html?#Note_for_Troubleshooting_LIRC_Make)

The above post and version did not work on feisty --

Heres how to create ledxmit on Feisty:

Here it is.

Before starting make sure some necessary utilities are installed:

```
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install setserial
```


**INSTALLING**

Get LIRC version 0.8.2 from the LIRC download page 
 ```
cd ~
 mkdir myth-ledxmit ; cd myth-ledxmit
 wget http://internap.dl.sourceforge.net/sourceforge/lirc/lirc-0.8.2.tar.bz2
 bzip2 -d *bz2 ; tar xf *tar

```

Create this shell script that will create a new version of lirc called ledxmit that is independent of the regular lirc.

gedit ~/myth-ledxmit/myth-ledxmit82-feisty.sh

cut and paste the following into the file
```

#!/bin/bash
#
# myth-ledxmit.sh
#
# by jds-myth !at! losdos.dyndns.org
# portions by rwraithr !at! iwamble.net
#
# for details on how and why to use this script, see
# http://losdos.dyndns.org:8080/public/mythtv-info/MythTV_DISH_IR_LED_TX_via_Modified_LIRC.html
#
set -e
#
#
if [ ! $# -eq 1 ]
then
  echo "usage: $0 lirc-directory"
  exit 1
fi

if [ ! -d $1 ]
then
  echo "error: directory '$1' not found."
  exit 1
fi

rm -rf myth-ledxmit.WIP
echo "$0: Copying lirc source directory..."
cp -r $1 myth-ledxmit.WIP

cd myth-ledxmit.WIP
if [ $? -ne 0 ]
then
  echo "error: unable to cd to 'myth-ledxmit.WIP'."
  exit 1
fi

echo "$0: Moving lirc directories"
mv ./drivers/lirc_atiusb   ./drivers/ledxmit_atiusb
mv ./drivers/lirc_mceusb   ./drivers/ledxmit_mceusb
mv ./drivers/lirc_bt829    ./drivers/ledxmit_bt829
mv ./drivers/lirc_dev      ./drivers/ledxmit_dev
mv ./drivers/lirc_gpio     ./drivers/ledxmit_gpio
mv ./drivers/lirc_i2c      ./drivers/ledxmit_i2c
mv ./drivers/lirc_it87     ./drivers/ledxmit_it87
mv ./drivers/lirc_parallel ./drivers/ledxmit_parallel
mv ./drivers/lirc_serial   ./drivers/ledxmit_serial
mv ./drivers/lirc_sir      ./drivers/ledxmit_sir
mv ./drivers/lirc_sasem    ./drivers/ledxmit_sasem
mv ./drivers/lirc_igorplugusb ./drivers/ledxmit_igorplugusb

# lirc 0.7.2 adders
mv ./drivers/lirc_imon     ./drivers/ledxmit_imon
mv ./drivers/lirc_streamzap  ./drivers/ledxmit_streamzap
mv ./drivers/lirc_cmdir    ./drivers/ledxmit_cmdir
mv ./drivers/lirc_mceusb2  ./drivers/ledxmit_mceusb2

# lirc 0.8.2 adders
mv ./drivers/lirc_ttusbir ./drivers/ledxmit_ttusbir

echo "$0: Moving lirc files"
find . -name '*lirc*' -print > lircfiles.txt
for i in `cat lircfiles.txt`
  do
    if [ -f $i ] ; then
    NewFileName=`echo $i | sed 's/lirc/ledxmit/'`
    mv $i $NewFileName
  fi
done

echo "$0: Renaming lirc vars in files"
find . | xargs grep -l lirc > lircvars.txt
for i in `cat lircvars.txt`
  do
if [ -f $i ] ; then
    cat $i | sed 's/lirc/ledxmit/g' > $i.newfile
    mv $i.newfile $i
  fi
done

echo "$0: Renaming LIRC vars in files"
find . | xargs grep -l LIRC > LIRCvars.txt
for i in `cat LIRCvars.txt`
  do
    if [ -f $i ] ; then
    cat $i | sed 's/LIRC/LEDXMIT/g' > $i.newfile
    mv $i.newfile $i
  fi
done

echo "$0: Restoring exec permissions"
chmod +x ./configure ./*.sh

# while the following configure statement makes the default port COM2 (= /dev/ttyS1),
# there are examples later in this document which show how to tell the driver that you
# in fact want to use COM1 (=/dev/ttyS0) instead.

echo "$0: Running configure"
./configure --program-prefix=ledxmit- --prefix=/usr/local/lirc-ledxmit \
  --with-major=72 --with-port=0x2f8 --with-irq=3 --with-transmitter \
  --enable-sandboxed --with-driver=serial

echo "$0: Running make"
make
echo "$0: Complete"

```

Make it executable
```
chmod 755 ~/myth-ledxmit/myth-ledxmit82-feisty.sh
```

Run the script
```
~/myth-ledxmit/myth-ledxmit82-feisty.sh lirc-0.8.2
```

Change to the myth-ledxmit.WIP directory
```
cd ~/myth-ledxmit/myth-ledxmit.WIP
```

Install
```
sudo make install
```

N[B]OTE: All of the newly created LIRC executables are copied by "make install" to a separate tree under /usr/local/lirc-ledxmit.
No MythTV nor Linux configuration files are changed during this process.
[/B]



**SETTING UP**



_**CREATE /etc/ledxmitd.conf**_ will need to be setup with your remote codes

```
sudo gedit /etc/ledxmitd.conf
```

see this link [http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/)

You can create your own if your cable or sat box is not listed.

Mine was a visonetics and contains the following:
```

#
# this config file was automatically generated
# using WinLIRC 0.6.5 (LIRC 0.6.1pre3) on Thu Apr 20 00:35:35 2006
#
# contributed by Tom Graham
#
# brand:             Visionetics
# model:
# supported devices:
#

begin remote

  name  visionetics
  bits           16
  flags SPACE_ENC
  eps            25
  aeps          100

  header       8972  4550
  one           538   586
  zero          538  1716
  ptrail        538
  repeat       8986  2284
  pre_data_bits   16
  pre_data       0x9E29
  gap          40153
  toggle_bit      0


      begin codes
          1                        0x0000000000007F80
          2                        0x000000000000BF40
          3                        0x0000000000003FC0
          4                        0x000000000000DF20
          5                        0x0000000000005FA0
          6                        0x0000000000009F60
          7                        0x0000000000001FE0
          8                        0x000000000000EF10
          9                        0x0000000000006F90
          0                        0x000000000000AF50
          ok                       0x0000000000008F70
          volup                    0x00000000000047B8
          voldown                  0x000000000000F708
          chup                     0x00000000000017E8
          chdown                   0x00000000000037C8
          mute                     0x00000000000057A8
          exit                     0x000000000000CF30
          power                    0x000000000000B748
      end codes

end remote


```





**_Create /etc/modutils/lirc-ledxmit_**

```
sudo gedit /etc/modutils/lirc-ledxmit
```

Insert the following for COM2 Serial IR Blaster
```
# FILE:  /etc/modutils/lirc-ledxmit
alias char-major-72 ledxmit_serial
below ledxmit_serial ledxmit_dev
# !!! note DEFAULT is COM2 !!!  
# for COM1, simply uncomment the following:
# options ledxmit_serial irq=4 io=0x3f8
# for COM2, do nothing, or uncomment the following:
 options ledxmit_serial irq=3 io=0x2f8

```

Save the file

Add the new modules list

```
sudo  /sbin/update-modules
```

Make the device node
```
sudo /bin/mknod /dev/ledxmit c 72 0
```

Disable the regular serial port driver
```
sudo /bin/setserial /dev/ttyS1 uart none     # (IS for COM2 use /dev/ttyS0 for COM1)
```

Install the ledxmit_serial module:
```
sudo /sbin/modprobe ledxmit_serial
```

****** IF THE ABOVE COMMAND GIVES AN ERROR TRY THIS INSTEAD  (THANKS to dannyboy79)
```
sudo depmod -ae
sudo /sbin/modprobe ledxmit_serial

```

Make sure it's working
```
sudo lsmod | grep ledxmit
```
you should see the following:

ledxmit_serial          7104   0
ledxmit_dev             8560   1  [ledxmit_serial]


Start up the ledxmit daemon
```
sudo  /usr/local/lirc-ledxmit/sbin/ledxmit-ledxmitd -L /tmp/ledxmitd.log
```
(this starts the deamon ledxmitd and creates a listening socket at /dev/ledxmitd)

Verify both ledxmit-related devices are now present and have the proper attributes:
```
ls -sl /dev/led*
```
you should see:

   0 crw-r--r--    1 root     root      72,   0 May  4 20:57 /dev/ledxmit
   0 srw-rw-rw-    1 root     root            0 May  4 20:57 /dev/ledxmitd


Create startup scrit
```
sudo gedit /etc/init.d/startledxmit.sh
```

Insert the following into it.
```

/sbin/update-modules
/bin/mknod /dev/ledxmit c 72 0
/bin/setserial /dev/ttyS1 uart none     # use this for COM2
#/bin/setserial /dev/ttyS0 uart none     # (or use /dev/ttyS0 for COM1)
/sbin/modprobe ledxmit_serial
/usr/local/lirc-ledxmit/sbin/ledxmit-ledxmitd -L /tmp/ledxmitd.log

```
save the file and exit gedit

Make it executable
```
sudo chmod 755 /etc/init.d/startledxmit.sh
```

Set the script to start
```
sudo gedit /etc/rc.local
```

add the following line before exit 0

```
/bin/sh /etc/init.d/startledxmit.sh
```
save the file and exit gedit



**TEST IT**

This is assuming you have a visionetics remote devicedescribed  in /etc/ledxmit.conf


The command below would turn  a visionetics device on or off

```
/usr/local/lirc-ledxmit/bin/ledxmit-irsend SEND_ONCE visionetics  power
```

Your remote device will be different so adjust the above command

see also 
google for irsend for syntax



Change Channel Script.

To get MythTv to use the Blaster create a change channel script.  --> See it  here:[http://losdos.dyndns.org:8080/public/mythtv-info/MythTV_DISH_IR_LED_TX_via_Modified_LIRC.html?#Note_for_Troubleshooting_LIRC_Make](http://losdos.dyndns.org:8080/public/mythtv-info/MythTV_DISH_IR_LED_TX_via_Modified_LIRC.html?#Note_for_Troubleshooting_LIRC_Make)


EXAMPLE:
```
sudo gedit /usr/local/bin/change_chan.sh
```


Add this to it (change for your remote)
```
#!/bin/sh
REMOTE_NAME=visionetics  #note, ensure that the REMOTE_NAME is the same as what you have in your /etc/ledxmitd.conf file
for digit in $(echo $1 | sed -e 's/./& /g'); do
/usr/local/lirc-ledxmit/bin/ledxmit-irsend SEND_ONCE $REMOTE_NAME $digit
sleep 0.4 # note, you may have to tweak the interdigit delay up a bit, depending on your DISH receiver model
done
```

Change permissions

```
chmod 755 /usr/local/bin/change_chan.sh
```

Test it.
```

change_chan.sh 201
```

should change the box to channel 201


NOTE:
If you have a digital camera with a screen viewer you can see if the blaster is working by looking at the irblaster through the camera while running the script above.

---

### Post by superm1 on 2007-09-14
> **tagra123 said:**
> HOW TO MYTHTV LIRC SERIAL IRBLASTER 

Making lirc work in any version of Ubuntu seems more difficult than necessary.



Take a look at the Gutsy guides.  I've been working on improving the situation.  
I've added pre-selection of a lircd.conf, automatic lircrc generation, and ship kernel modules with the kernel.

If you can test and/or have any further recommendations, please let me know while there is still time in the development cycle.

> 
This has been adapted from another how to located here:

[http://losdos.dyndns.org:8080/public/mythtv-info/MythTV_DISH_IR_LED_TX_via_Modified_LIRC.html?#Note_for_Troubleshooting_LIRC_Make](http://losdos.dyndns.org:8080/public/mythtv-info/MythTV_DISH_IR_LED_TX_via_Modified_LIRC.html?#Note_for_Troubleshooting_LIRC_Make)

The above post and version did not work on feisty --

What didn't work with the feisty setup?  Feisty is just using an older checkout of lirc than 0.8.2.  You can still build serial modules and configure it just fine.

> 
Heres how to create ledxmit on Feisty:

Here it is.

Before starting make sure some necessary utilities are installed:

```
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install setserial
```**INSTALLING**

Get LIRC version 0.8.2 from the LIRC download page 
 ```
cd ~
 mkdir myth-ledxmit ; cd myth-ledxmit
 wget http://internap.dl.sourceforge.net/sourceforge/lirc/lirc-0.8.2.tar.bz2
 bzip2 -d *bz2 ; tar xf *tar

```Create this shell script that will create a new version of lirc called ledxmit that is independent of the regular lirc.

gedit ~/myth-ledxmit/myth-ledxmit82-feisty.sh

cut and paste the following into the file
```

#!/bin/bash
#
# myth-ledxmit.sh
#
# by jds-myth !at! losdos.dyndns.org
# portions by rwraithr !at! iwamble.net
#
# for details on how and why to use this script, see
# http://losdos.dyndns.org:8080/public/mythtv-info/MythTV_DISH_IR_LED_TX_via_Modified_LIRC.html
#
set -e
#
#
if [ ! $# -eq 1 ]
then
  echo "usage: $0 lirc-directory"
  exit 1
fi

if [ ! -d $1 ]
then
  echo "error: directory '$1' not found."
  exit 1
fi

rm -rf myth-ledxmit.WIP
echo "$0: Copying lirc source directory..."
cp -r $1 myth-ledxmit.WIP

cd myth-ledxmit.WIP
if [ $? -ne 0 ]
then
  echo "error: unable to cd to 'myth-ledxmit.WIP'."
  exit 1
fi

echo "$0: Moving lirc directories"
mv ./drivers/lirc_atiusb   ./drivers/ledxmit_atiusb
mv ./drivers/lirc_mceusb   ./drivers/ledxmit_mceusb
mv ./drivers/lirc_bt829    ./drivers/ledxmit_bt829
mv ./drivers/lirc_dev      ./drivers/ledxmit_dev
mv ./drivers/lirc_gpio     ./drivers/ledxmit_gpio
mv ./drivers/lirc_i2c      ./drivers/ledxmit_i2c
mv ./drivers/lirc_it87     ./drivers/ledxmit_it87
mv ./drivers/lirc_parallel ./drivers/ledxmit_parallel
mv ./drivers/lirc_serial   ./drivers/ledxmit_serial
mv ./drivers/lirc_sir      ./drivers/ledxmit_sir
mv ./drivers/lirc_sasem    ./drivers/ledxmit_sasem
mv ./drivers/lirc_igorplugusb ./drivers/ledxmit_igorplugusb

# lirc 0.7.2 adders
mv ./drivers/lirc_imon     ./drivers/ledxmit_imon
mv ./drivers/lirc_streamzap  ./drivers/ledxmit_streamzap
mv ./drivers/lirc_cmdir    ./drivers/ledxmit_cmdir
mv ./drivers/lirc_mceusb2  ./drivers/ledxmit_mceusb2

# lirc 0.8.2 adders
mv ./drivers/lirc_ttusbir ./drivers/ledxmit_ttusbir

echo "$0: Moving lirc files"
find . -name '*lirc*' -print > lircfiles.txt
for i in `cat lircfiles.txt`
  do
    if [ -f $i ] ; then
    NewFileName=`echo $i | sed 's/lirc/ledxmit/'`
    mv $i $NewFileName
  fi
done

echo "$0: Renaming lirc vars in files"
find . | xargs grep -l lirc > lircvars.txt
for i in `cat lircvars.txt`
  do
if [ -f $i ] ; then
    cat $i | sed 's/lirc/ledxmit/g' > $i.newfile
    mv $i.newfile $i
  fi
done

echo "$0: Renaming LIRC vars in files"
find . | xargs grep -l LIRC > LIRCvars.txt
for i in `cat LIRCvars.txt`
  do
    if [ -f $i ] ; then
    cat $i | sed 's/LIRC/LEDXMIT/g' > $i.newfile
    mv $i.newfile $i
  fi
done

echo "$0: Restoring exec permissions"
chmod +x ./configure ./*.sh

# while the following configure statement makes the default port COM2 (= /dev/ttyS1),
# there are examples later in this document which show how to tell the driver that you
# in fact want to use COM1 (=/dev/ttyS0) instead.

echo "$0: Running configure"
./configure --program-prefix=ledxmit- --prefix=/usr/local/lirc-ledxmit \
  --with-major=72 --with-port=0x2f8 --with-irq=3 --with-transmitter \
  --enable-sandboxed --with-driver=serial

echo "$0: Running make"
make
echo "$0: Complete"

```Make it executable
```
chmod 755 ~/myth-ledxmit/myth-ledxmit82-feisty.sh
```Run the script
```
~/myth-ledxmit/myth-ledxmit82-feisty.sh lirc-0.8.2
```Change to the myth-ledxmit.WIP directory
```
cd ~/myth-ledxmit/myth-ledxmit.WIP
```Install
```
sudo make install
```N[B]OTE: All of the newly created LIRC executables are copied by "make install" to a separate tree under /usr/local/lirc-ledxmit.
No MythTV nor Linux configuration files are changed during this process.
[/B]

Seems a bit unnecessary to have a whole lirc setup that everything is renamed to ledxmit?  The lirc_serial module shouldn't conflict with much of anything anyhow.


> 
**SETTING UP**



_**CREATE /etc/ledxmit.conf**_ will need to be setup with your remote codes

see this link [http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/)

You can create your own if your cable or sat box is not listed.

Mine was a visonetics and contains the following:
```

#
# this config file was automatically generated
# using WinLIRC 0.6.5 (LIRC 0.6.1pre3) on Thu Apr 20 00:35:35 2006
#
# contributed by Tom Graham
#
# brand:             Visionetics
# model:
# supported devices:
#

begin remote

  name  visionetics
  bits           16
  flags SPACE_ENC
  eps            25
  aeps          100

  header       8972  4550
  one           538   586
  zero          538  1716
  ptrail        538
  repeat       8986  2284
  pre_data_bits   16
  pre_data       0x9E29
  gap          40153
  toggle_bit      0


      begin codes
          1                        0x0000000000007F80
          2                        0x000000000000BF40
          3                        0x0000000000003FC0
          4                        0x000000000000DF20
          5                        0x0000000000005FA0
          6                        0x0000000000009F60
          7                        0x0000000000001FE0
          8                        0x000000000000EF10
          9                        0x0000000000006F90
          0                        0x000000000000AF50
          ok                       0x0000000000008F70
          volup                    0x00000000000047B8
          voldown                  0x000000000000F708
          chup                     0x00000000000017E8
          chdown                   0x00000000000037C8
          mute                     0x00000000000057A8
          exit                     0x000000000000CF30
          power                    0x000000000000B748
      end codes

end remote


```

**_Create /etc/modutils/lirc-ledxmit_**

```
sudo gedit /etc/modutils/lirc-ledxmit
```Insert the following for COM2 Serial IR Blaster
```
# FILE:  /etc/modutils/lirc-ledxmit
alias char-major-72 ledxmit_serial
below ledxmit_serial ledxmit_dev
# !!! note DEFAULT is COM2 !!!  
# for COM1, simply uncomment the following:
# options ledxmit_serial irq=4 io=0x3f8
# for COM2, do nothing, or uncomment the following:
 options ledxmit_serial irq=3 io=0x2f8

```Save the file

Add the new modules list

```
sudo  /sbin/update-modules
```Make the device node
```
sudo /bin/mknod /dev/ledxmit c 72 0
```Disable the regular serial port driver
```
sudo /bin/setserial /dev/ttyS1 uart none     # (IS for COM2 use /dev/ttyS0 for COM1)
```Install the ledxmit_serial module:
```
sudo /sbin/modprobe ledxmit_serial
```Make sure it's working
```
sudo lsmod | grep ledxmit
```you should see the following:

ledxmit_serial          7104   0
ledxmit_dev             8560   1  [ledxmit_serial]


Start up the ledxmit daemon
```
sudo  /usr/local/lirc-ledxmit/sbin/ledxmit-ledxmitd -L /tmp/ledxmitd.log
```(this starts the deamon ledxmitd and creates a listening socket at /dev/ledxmitd)

Verify both ledxmit-related devices are now present and have the proper attributes:
```
ls -sl /dev/led*
```you should see:

   0 crw-r--r--    1 root     root      72,   0 May  4 20:57 /dev/ledxmit
   0 srw-rw-rw-    1 root     root            0 May  4 20:57 /dev/ledxmitd


Create startup scrit
```
sudo gedit /etc/startledxmit.sh
```Insert the following into itL
```

/sbin/update-modules
/bin/mknod /dev/ledxmit c 72 0
/bin/setserial /dev/ttyS1 uart none     # use this for COM2
/bin/setserial /dev/ttyS1 uart none     # (or use /dev/ttyS0 for COM1)
/sbin/modprobe ledxmit_serial
/usr/local/lirc-ledxmit/sbin/ledxmit-ledxmitd -L /tmp/ledxmitd.log

```save the file and exit gedit

Make it executable
```
sudo chmod 755 /etc/init.d/startledxmit.sh
```Set the script to start
```
sudo gedit /etc/rc.local
```add the following line before exit 0

```
/bin/sh /etc/init.d/startledxmit.sh
```save the file and exit gedit



**TEST IT**

This is assuming you have a visionetics remote devicedescribed  in /etc/ledxmit.conf


The command below would turn  a visionetics device on or off

```
/usr/local/lirc-ledxmit/bin/ledxmit-irsend SEND_ONCE visionetics  power
```Your remote device will be different so adjust the above command

see also 
google for irsend for syntax



Change Channel Script.

To get MythTv to use the Blaster create a change channel script.  --> See it  here:[http://losdos.dyndns.org:8080/public/mythtv-info/MythTV_DISH_IR_LED_TX_via_Modified_LIRC.html?#Note_for_Troubleshooting_LIRC_Make](http://losdos.dyndns.org:8080/public/mythtv-info/MythTV_DISH_IR_LED_TX_via_Modified_LIRC.html?#Note_for_Troubleshooting_LIRC_Make)

It really would be preferable to do a setup that doesn't require a user to manually go and compile so many things.  The LIRC packages for feisty do support building all the modules you select and install them via a simple set of module assistant commands on the bottom of the feisty LIRC pages.

---

### Post by tagra123 on 2007-09-14
First of all I appreciate you replying.  

Certain thing would be nice if they just worked without so much fiddling.

You are right. Mine takes about 15 minutes to setup and requires a compile. That is a drawback but on if you can get the other to work which I could not.

Perhaps if  I modified my startup script to lirc, lirc would work correctly too.

**_The HUGE advantage_**, in my opinion, is that this is independent of lirc  and  " it just works" if you do the steps in post #1. No tracking down why its not working it just works. And if you need a serial blaster or  a serial receiver and built in lirc you can have it

Heres the problem I ran into with the regular setup and it may have something to do with mythtv interfering. I have no idea really. Everything using your Feisty guide seemed  to work and then just stop.

I went through all the steps in your how to. -- lirc works. Reboot the computer everything loads but irsend will not work. It would just stop working without a reboot too. I looked at the logs but it wasnt telling me anything useful to diagnose the problem

One other thing.

I would be glad to help create or work with you on a gui to select the remote or another method. I've often though that this would be a cool addition to lirc. Maybe a sqlite database of all the code where you could select your remote / set top box and be on your way -- it could copy the selected box to lircd.conf.   

What would be very nice with lirc is if it as set up like the universal remotes are. click a button enter a remote code and the remote is selected and if that doesnt work have a learn button where it can try to learn the box you are using. 

I really do believe something in mythtv messes with lirc. To make a long story short it seems like the lirc modules unloads itself after an irsend, but not when using my method in post#1.  Beats me???? 

Now using my setup the ledxmit has been running 3 or 4 days now with 0 problems.

I mainly posted the original article so that folks already distressed with the datadirect disappearing, and having to upgrade a working system,  could get their setup working quickly again.

I think the real "magic"  / "fix" in the lirc occurs in the startup script though. Not sure why -- maybe you could shed some light on this.

I have a complete transcript of my install using your feisty guide (It didn't work for me) I can send you a copy. You need to use script.sh to play it back.

I appreciate the guides. It would be very very nice if mythtv had a copy of yours or my lirc (don't care as long as it works) as a part of the package. Even if it was caled mythserialblaster -- click a couple of buttons and it works. Now that would be useful.

Thanks for replying.

---

### Post by dannyboy79 on 2007-10-03
well, this isn't working for me. I followed the guide to a tee and I get this when trying to load the module using sudo /sbin/modprobe ledxmit_serial:

FATAL: Module ledxmit_serial not found.

Can you please help? I have been trying to get channel changing working forever! I have a very basic serial IR Blaster from irblaster.info. ANything else I should post I will, but I would really appreciate your help here.

UPDATE:
ok, your guide is missing the fact that one must run this command prior to loading the module with sudo /sbin/modprobe

sudo depmod -ae

after I ran that, I then did not get an error trying to load the module, then also sudo lsmod | grep led shows these results:
ledxmit_serial         15748  0
ledxmit_dev            16244  1 ledxmit_serial

You may want to update your guide unless I am wrong about this???

Other issues I found.

When I ran ls -la /dev/ | grep led
 I actually get 3 results instead of 2 like what you have, mine shows
crw-r--r--  1 root   root     72,   0 2007-10-03 09:30 ledxmit
crw-rw----  1 root   root     72,   0 2007-10-03 10:18 ledxmit0
srw-rw-rw-  1 root   root           0 2007-10-03 10:23 ledxmitd

You tell us to create this file: sudo gedit /etc/startledxmit.sh
but then later you tell us to make sudo gedit /etc/init.d/startledxmit.sh executable, so obviously this fails. You need to update sudo gedit /etc/startledxmit.sh so that it has the init.d directory within it, correct? So it would:
sudo gedit /etc/init.d/startledxmit.sh

Maybe you want to mention how does one know whether to use ttys0 or ttys1? I don't know what COM port my serial port uses? Should I?? I can see by issuing dmesg | grep ttyS0 that it's: [    1.377607] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.378222] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
so that must mean that it is using ttyS0 which is COM1 correct? Does this mean I have to go back through the guide and change everything from com2 config to com1???

The link for getting a channel changing script is dead, why not just paste this here?
#!/bin/sh
REMOTE_NAME=SA2000 #note, ensure that the REMOTE_NAME is the same as what you have in your /etc/ledxmitd.conf file
for digit in $(echo $1 | sed -e 's/./& /g'); do 
  /usr/local/lirc-ledxmit/bin/ledxmit-irsend SEND_ONCE $REMOTE_NAME $digit
  sleep 0.4  # note, you may have to tweak the interdigit delay up a bit, depending on your DISH receiver model
done

---

### Post by tagra123 on 2007-10-04
I dont recall having to use depmod when testing or working with my  setup. It is good to mention this.  though.


Thank for pointing out 

sudo gedit /etc/startledxmit.sh  should have read 

sudo gedit /etc/init.d/startledxmit.sh it has been fixed in the original post.

About the Com ports.  Mine are marked on the back of the PC. On a desktop the two ports are usually together . Normally COM1 is above COM2.

Rather than recompile you can change it here 

sudo gedit /etc/init.d/startledxmit.sh

/sbin/update-modules
/bin/mknod /dev/ledxmit c 72 0
#/bin/setserial /dev/ttyS1 uart none     # use this for COM2
/bin/setserial /dev/ttyS0 uart none     # (or use /dev/ttyS0 for COM1)
/sbin/modprobe ledxmit_serial
/usr/local/lirc-ledxmit/sbin/ledxmit-ledxmitd -L /tmp/ledxmitd.log

or just plug it into the other port.

The link isn't dead -- it's just slow.  I pointed people to this link in case they wanted more than one example with details.

---

### Post by dannyboy79 on 2007-10-04
ok, thank you for the response, so you're saying that all I have to fix is how ledxmit daemon is started?? Just comment out the ttyS1 and make it ttyS0 based on what dmesg shows? I don't think that would work because COM1 is on a different IRQ than what the this version of lirc (ledxmit name) was configured with, so how would this work???? My dmesg shows:
[    1.521406] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.522019] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
so that would mean to me that me that the lirc should be configured with COM1 support, not COM2 support. OR are you saying that LIRC can be left configured with COM2 support only but when I start ledxmit daemon, it'll somehow make LIRC use COM1?

As a side note, I myself don't have 2 serial ports with the same male connector, I only have 1. The serial ir blaster I bought is a female connector, so I don't have a choice which port I put it in  unless I buy an adapter. In fact I have never seen a motherboard with 2 serial ports that were the same connection type. WHich maybe again would be a good thing to point out.

I also think that this area is wrong for me since I need to use the  COM1 port:
/etc/modutils/lirc-ledxmit
# FILE:  /etc/modutils/lirc-ledxmit
alias char-major-72 ledxmit_serial
below ledxmit_serial ledxmit_dev
# !!! note DEFAULT is COM2 !!!  
# for COM1, simply uncomment the following:
# options ledxmit_serial irq=4 io=0x3f8
# for COM2, do nothing, or uncomment the following:
 options ledxmit_serial irq=3 io=0x2f8

shouldn't I update this as well??


Also, do you have any comments regarding the fact that I get 3 different ledxmit's within the /dev/ directory?
crw-r--r--  1 root   root     72,   0 2007-10-03 10:59 ledxmit
crw-rw----  1 root   root     72,   0 2007-10-03 10:59 ledxmit0
srw-rw-rw-  1 root   root           0 2007-10-04 15:04 ledxmitd

I did try this guide from the original post but it didn't work, so I wondering if something is still left behind from when I tried the first time??? I hate linux for not really having an uninstall feature for compiled stuff. I know there's sudo make uninstall, is that what I should use to redo this all???? How do I go around and ensure that I remove what this has done so I can redo it correctly?


The last thing I just noticed. Your guide says to create a ledxmit.conf file, well when I try to start up ledxmit, it says that a ledxmitd.conf file doesn't exist. So your guide should say that a ledxmitd.conf file should be created versus just the name being ledxmit.conf. Right??
Unless there should be a ledxmit.conf as well as a ledxmitd.conf for the daemon but if that's the case, what's suppose to go within ledxmitd.conf?

Thanks again for your help, I have been trying to get control of my STB for over 40 hours without success of firewire channel changing and now this, it's just rediculious how hard this is to get working. Any help regarding new questions would be appreciated.

---

### Post by tagra123 on 2007-10-04
1st
Sorry for the typos in the original post. Fixing them,


Check your bios setting to see for sure which com port is wwhich -- irq, address, etc.

For testing disconnect everything  except the irblaster from the com port. It sounds like you have two devices on the same port???

Plug the irblaster into com1 and proceed with the instructions for /etc/modutils/lirc-ledxmit

Not sure why you are getting ledxmit and ledxmit0 except that maybe its seeing two com devices ????

The ledxmit.conf should be ledxmitd.conf --typo and is fixed in the original post

as far as uninstalling -- recompiling and installing should install the newly compiled version. you should be able to go to the directory containing the ledxmit that you installed from and type ```
sudo make uninstall
```

Google for make uninstall and make clean.


You can check for errors in /tmp/ledxmitd.log

cat /tmp/ledxmitd.log

Post the output here if it still isn't working.

---

### Post by dannyboy79 on 2007-10-05
ok, well I got ledxmit sending the signal to the box ( i have an ir blaster that lights up when it works) BUT the damn cable box does nohting. I tried to use both irw and irrecord but the pvr-350 ir reciver just doesn't see any button presses from this damn TWC STB remote. it's a contec rt-u62cp-1.17. I have even played around with the frequency as well as the gap within a ledxmitd.conf that someone said works with  a Scientific Atlanta 3200 stb to no success. So now I am f__ed on all channel changing solutions and can't figure out how to record premiums stations. 

Seriously thinkinbg aboiut getting TWC DVR for this and leaving mythtv to record ananlog only.

HOw can I figure out what codes my STB want's?????

---

### Post by dannyboy79 on 2007-10-06
FINALLY GOT IT WORKING. It was the ledxmitd.conf that wasn't correct. The Scientific Atlanta 2000 config within sourceforge lirc remotes wasn't working but the SAE8000 does. This was is for some reason saved under the name AT8400, which after you click on that one, the name of the remote within there is a SAE8000. Which is the Scientific Atlanta 8000 series STB's. Then I just added a "select" for the channel changing to happen right away. So my channel change command is this:

#!/bin/sh
REMOTE_NAME=SAE8000 #note, ensure that the REMOTE_NAME is the same as what you have in your /etc/ledxmitd.conf file
for digit in $(echo $1 | sed -e 's/./& /g'); do 
/usr/local/lirc-ledxmit/bin/ledxmit-irsend SEND_ONCE $REMOTE_NAME $digit
sleep 0.4  # note, you may have to tweak the interdigit delay up a bit, depending on your DISH receiver model
done
/usr/local/lirc-ledxmit/bin/ledxmit-irsend SEND_ONCE $REMOTE_NAME select

---

### Post by yotux on 2007-10-07
I see that this thread is talking about feisty allot, I am using Gusty.  I have bought a Ir blaster R232 from Irblaster.info.  It is a serial blaster and I am at a lose to get it installed.

I have two Serial ports.

Com 1 is being used for a serial modem,

Com 2 is being used or to be used for the IRblaster.

I am running Gusty and using Mythbuntu,  willing to change to normal ubuntu if needed.

I assume R232 is just a matter of the chip compent.  Please give me some guidence to figure this out.

Nathan aka Yotux

---

### Post by dannyboy79 on 2007-10-08
If you want to create another instance of lirc than this is the guide for you. BUT according to superm1, this is unneccessary. I myself can't tell you how to get one instance of lircd to not only receive signals but also send them so I just followed the guide and it worked like a treat! 

just follow the guide, I found the typos and what not and he has updated the guide so it should be a matter of following it word for word. You have the same exact IR serial blaster as I do (from irblaster.info) and it works when you follow the guide! The only thing the guide doesn't have for you is the /etc/lircd.conf which defines the ir signals with the buttons on the remote you'll want to use to control your computer (it'll contain IR signal codes and the button for that ir signal), then, if you want to be able to control mythtv with that remote you'll need a /home/username/.mythtv/lircrc
 file so that lircd can map those buttons defined with ir signal codes in lircd.conf to actual keyboard strokes so that when you're in mythtv and you hit the remote button channel up, that file will make that channel up from the remote be a keyboard stroke of the up arrow (so and so forth). Last but not least and most important you'll need a /etc/ledxmitd.conf, this is the file that is the button ir signals that you need to send to your STB, dish box, or Direct TV box. This was my holdup the whole time, my ir blaster was sending signals but since they weren't the right signals at first, it didn't work. Once I found that SAE8000 lircd.conf file, saved it as /etc/ledxmitd.conf and restarted my machine, I WAS GOLDEN.

So just follow the guide and post back when you need help, I just did this and I can help completely if you have a SA 3250HD Set Top Box and a PVR-350. If you have other equipment I can try to help. Good luck!

PS, since you have your ir blaster hooked to COM2, this guide is perfect because that's the default setup where as mine wasn't. My IR blaster was on COM1 based on what "dmesg | grep ttyS" shows after booting up. See my example of why I know that I needed to use COM1 for my setup (means compiling it different by changing the downloadable script so that it does the ./configure differently)

cat /var/log/dmesg | grep ttyS
[    1.521568] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.522180] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

COM1 should be 0x3f8 (irq = 4)
and 
COM2 should be 0x2f8 (irq = 3)

---

### Post by hchaos on 2007-10-21
Thanks for the guide, it's been very helpful so far. I have the same serial device (from irblaster.info) that you guys do, and I cannot seem to get it to work. I've configured everything and verified there are no errors. I set up my remote for my Pioneer stereo, and tried to control it with no luck. Every time I try to send a command, I see this from /tmp/ledxmitd.log:

Oct 21 16:41:29 mokey ledxmitd: accepted new client on /dev/ledxmitd

Oct 21 16:41:59 mokey ledxmitd: removed client


It looks like everything should work, but it does not. I used my digital camera to see if I could detect anything from the irblaster and when I send a command it does nothing. I verified using a remote that the camera can properly convert the infrared light to the human-visible spectrum.

Any ideas? I have configured COM1 (like Dannyboy) as that is what my system has. I have nothing else plugged in. Not sure where to look next to diagnose this issue. I suppose it's possible the irblaster is connected to the wrong pin on the db9 connector. Could I test the irblaster by adding voltage to the line? I don't want to blow it out so I'm not sure how much I should apply.

---

### Post by xmrkite on 2008-04-02
Hello all. I hope someone is still paying attention to this forum. I tried using this guide and followed it to the letter, but i am unable to get it to work.

I have the serial blaster from irblaster.info.

Upon trying to change channels, i don't get any errors, and from the command line, all seems to work just fine, however...the blaster is not emitting any ir signal, as my digi cam was not able to see anything. I do have a usb blaster on this system, and that one does show up on my digi cam (the ir light).

Also, i only have one serial port on this computer...and i left the original config alone, so it's trying to use com2. Do i even have com2 since there is only 1 port?

Any ideas for me?

Thank you.

---

### Post by dannyboy79 on 2008-04-03
what does this return?

dmesg | grep ttyS

---

### Post by Kepesk on 2008-04-03
Hello!

I would appear to be having the same issue as xmrkite here.  I have a Gutsy install, also with a serial blaster from irblaster.info.  I installed ledxmit using the instructions given here, and everything appeared to install fine.  I followed the steps to enable it for COM1 since I only have one port, and my motherboard manual says it should be COM1 (and trying it with COM2 gives me errors.

Basically, I plug the thing in, and test it, and the thing doesn't light up at all.

I installed WinLirc on a windows machine, and it lit up just fine, so I know the hardware is working and I can see the infared in my camera.

So I went back to my Ubuntu machine, and did some more investigation.  Testing the blaster using the instructions above inserts the correct messages into the log file:

Apr  2 18:56:39 Mordalfus ledxmitd: accepted new client on /dev/ledxmitd
Apr  2 18:56:39 Mordalfus ledxmitd: removed client

But the blaster doesn't light up.  I even tested it at a lower level by sending random text directly to /dev/ttyS0, it still fails to light up.  After some investigation, the only oddity in my setup is that when I run "ls -sl /dev/led*" I get:

0 crw-r--r-- 1 root root 72, 0 2008-04-02 18:31 /dev/ledxmit
0 crw-rw---- 1 root root 72, 0 2008-04-02 18:31 /dev/ledxmit0
0 srw-rw-rw- 1 root root     0 2008-04-02 18:31 /dev/ledxmitd

instead of the regular ledxmit and ledxmitd that the how to describes.  Could this be part of the problem?

Thanks!

EDIT: dmesg | grep ttyS returns the following:

[   43.439676] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   43.439829] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   43.440272] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

---

### Post by dannyboy79 on 2008-04-03
which one did you buy? the one that you can actually see the emitter blinking? or the one that you'd have to view through a view finder on a digital camera? I have the one that emits red flashes so I know it's working.

I have the same thing as you for ls -sl /dev/led* so I don't think that's it.

please show me the output of the following files:

/etc/modutils/lirc-ledxmit

/etc/init.d/startledxmit.sh

sudo lsmod | grep ledxmit

If you followed the guide I couldn't tell what would be stopping the blaster from at least emitting signals even if they are wrong???? Your dmesg output does look fishy, I only have one serial port on my motherboard and I get the following:
[    1.521723] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.522339] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

so maybe you're plugged into the 
[ 43.439829] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
although what's weird is that there is no 00:0X callout for it, on the serial8250. huh????

---

### Post by Kepesk on 2008-04-03
I bought the one where you can only see it through a camera, but I can see it working through my camera on winlirc.  Nada on my linux box with ledxmit.  And I agree with you that my Dmesg output looks wonky.  However, I'm fairly sure I'm plugged in to COM1, because my motherboard only has one com port, and my manual says it's COM1.  Here are the outputs you asked for.  Thanks!

/etc/modutils/lirc-ledxmit:

# FILE:  /etc/modutils/lirc-ledxmit
alias char-major-72 ledxmit_serial
below ledxmit_serial ledxmit_dev
# !!! note DEFAULT is COM2 !!!
# for COM1, simply uncomment the following:
 options ledxmit_serial irq=4 io=0x3f8
# for COM2, do nothing, or uncomment the following:
# options ledxmit_serial irq=3 io=0x2f8

/etc/init.d/startledxmit.sh:

/sbin/update-modules
/bin/mknod /dev/ledxmit c 72 0
#/bin/setserial /dev/ttyS1 uart none     # use this for COM2
/bin/setserial /dev/ttyS0 uart none     # (or use /dev/ttyS0 for COM1)
/sbin/modprobe ledxmit_serial
/usr/local/lirc-ledxmit/sbin/ledxmit-ledxmitd -L /tmp/ledxmitd.log

sudo lsmod | grep ledxmit:

ledxmit_serial         17704  0
ledxmit_dev            18888  1 ledxmit_serial

---

### Post by dannyboy79 on 2008-04-03
WOW, I am at a lose here. sorry I can't help anymore.

---

### Post by xmrkite on 2008-04-03
OK, i ran a 

dmesg | grep ttyS   and got this:

[    1.168721] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.168839] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.169291] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.169469] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   64.188760] ledxmit_serial: use 'setserial /dev/ttySX uart none'


I have the serial one with two heads but no flashy light, you have to use the digi cam (which i've seen that work by using my other blaster, a usb microsoft one.)

-Thanks for any ideas.

---

### Post by xmrkite on 2008-04-03
ok, here is some more info:


RAN THIS: lsmod | grep ledxmit

GOT THIS: ledxmit_dev            16244  0

RAN THIS: sudo /etc/modutils/lirc-ledxmit
GOT THIS: sudo: /etc/modutils/lirc-ledxmit: command not found

RAN THIS: /etc/init.d/startledxmit.sh
GOT THIS: /bin/mknod: `/dev/ledxmit': File exists

RAN THIS: dmesg | grep ttyS

GOT THIS:

[    1.168721] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.168839] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.169291] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.169469] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   64.188760] ledxmit_serial: use 'setserial /dev/ttySX uart none'



--thanks for any help you can provide.

---

### Post by jimbones on 2008-04-03
I'm gonna say hello here.

I've tried a lot of things, using Linux MCE, which is based on kubuntu, as well as knoppmyth, which is based on debian (it installs using knoppix).

I plugged my blaster in today and still no go.  The mythTV (I want MythTV to control my satellite box) has a setup script that seems to work fine, but nothing works.  I have tried the business with copying lirc over to ledxmit, remaking, etc with a homebrew blaster with no luck.

I have a video camera that sees ir (just point it at a remote control).

I guess I'll try the ledxmit install again now that I have a factory irblaster (the one from irblaster.org i think).

I'll report any successes.  I've downloaded the codes for the remote that came with my hd11 satellite box (directv).  According to the howto's I've seen, that can be renamed to irblasterd.conf (in the case of MythTv).

Any experience in this would be appreciated too.  MythTV is also part of LinuxMCE (an overbown media  center) which runs on kubuntu, so I know this is not a debian issue.

---

### Post by elj4176 on 2008-04-04
I'm on mythbuntu gutsy and have the irblaster.info serial blaster that lights up on com1. I followed the commands and everything seems to be working ok but it doesnt send any signals (no lights on the led).

any help would be appreciated.
thanks!

---

### Post by tagra123 on 2008-04-05
The instructiions and script should work for Gutsy too.  Give it a try and post results here.

If you follow the instructions in post #1 it should work.

Some have had good luck with the post made by superm1 (using the lirc from the repos)  but I could not get it to work and be dependable unless I compiled it myself.

A simple way to test is to point a digital camera at the IR LED and see if it lights up on the  LCD -- if it does -- you are in business and just need to get the conf file set up for your box.

Post any problems here -- I or someone will answer them for you.

---

### Post by tagra123 on 2008-04-05
> **elj4176 said:**
> I'm on mythbuntu gutsy and have the irblaster.info serial blaster that lights up on com1. I followed the commands and everything seems to be working ok but it doesnt send any signals (no lights on the led).

any help would be appreciated.
thanks!

I would check connection and/or try the other port. If its not working correctly the terminal will give some feedback. Also check the conf file too.  If all else fails then try a reboot. 

Like I said in the original post -- talking to a serial port should be much easier than it is.

---

### Post by tagra123 on 2008-04-05
> **elj4176 said:**
> I'm on mythbuntu gutsy and have the irblaster.info serial blaster that lights up on com1. I followed the commands and everything seems to be working ok but it doesnt send any signals (no lights on the led).

any help would be appreciated.
thanks!

I would check connection and/or try the other port. If its not working correctly the terminal will give some feedback. Also check the conf file too.  If all else fails then try a reboot. 

Like I said in the original post -- talking to a serial port should be much easier than it is. 

I encourage anyone who is able to get this working or gets stuck and is able to figure it out to post here for everyone's benefit.

---

### Post by tagra123 on 2008-04-05
> **jimbones said:**
> I'm gonna say hello here.

I've tried a lot of things, using Linux MCE, which is based on kubuntu, as well as knoppmyth, which is based on debian (it installs using knoppix).

I plugged my blaster in today and still no go.  The mythTV (I want MythTV to control my satellite box) has a setup script that seems to work fine, but nothing works.  I have tried the business with copying lirc over to ledxmit, remaking, etc with a homebrew blaster with no luck.

I have a video camera that sees ir (just point it at a remote control).

I guess I'll try the ledxmit install again now that I have a factory irblaster (the one from irblaster.org i think).

I'll report any successes.  I've downloaded the codes for the remote that came with my hd11 satellite box (directv).  According to the howto's I've seen, that can be renamed to irblasterd.conf (in the case of MythTv).

Any experience in this would be appreciated too.  MythTV is also part of LinuxMCE (an overbown media  center) which runs on kubuntu, so I know this is not a debian issue.


I haven't tried it on gutsy yet myself -- I do have Hardy running smoothly (not my myth box) and used the gustsy version of the mythtv frontend to watch while I work.

Note any errors, if any, you receive while compiling or following the steps in post 1 if something needs to be modified for Gutsy.  Post them here and I'll try to help you.  

Most of the Feisty setup for Myth went smoothly until I needed to get the remote working. It was a pain on breezy too.

I suppose if were were using one of the cards with built in IR it would work more smoothly using  the lirc that is in the repos but my experience is that the led-xmit works when the lirc module doesn't.

---

### Post by elj4176 on 2008-04-12
I havent had much time to look at it but I did just reboot the box. I'll try it again and report back. I was seeing info in the log like a previous poster and myth looked like it was trying to run the script because the screen wold freeze for a second when it was tying to change the channel.

edited to add:
ok - reboot did not solve my problem. The led on the eye is not lighting up at all. I did a ps ax and noticed that the chchange.sh script was still running. It was still trying to set the startup channel. 
I tried changing ownership and permissions of the script but it doesn't seem to matter. Now when I try to 'watch tv' the backend quits. 
I'm going to change the file permissions back to what they were and reboot again. Then I'll take my laptop down and go back thru the steps in this thread to see if everyhting is running as it is supposed to be. 

This may be a dumb question but what do you have in your backend setup for using the chchange script?
I have :
/usr/local/bin/chchange.sh

is that right? The script is located in /usr/local/bin/

---

### Post by elj4176 on 2008-04-12
zzz@zzz:~$ ps ax | grep led
 5381 ?        Ss     0:00 /usr/local/lirc-ledxmit/sbin/ledxmit-ledxmitd -L /tmp/ledxmitd.log
zzz@zzz:~$ dmesg | grep ttyS
[   13.595479] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.596715] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
zzz@zzz:~$ /usr/local/lirc-ledxmit/bin/ledxmit-irsend SEND_ONCE SAE8000  1
zzz@zzz:~$ ps ax
5264 ?        S      0:00 [lirc_dev]
5282 ?        Ss     0:00 /usr/sbin/lircd --device=/dev/lirc0
5381 ?        Ss     0:00 /usr/local/lirc-ledxmit/sbin/ledxmit-ledxmitd -L /tmp
6609 ?        Ssl    0:02 /usr/bin/mythfrontend.real --logfile /var/log/mythtv/
6653 ?        S      0:00 sudo sh /usr/local/bin/chchange.sh 30
6654 ?        S      0:00 sh -c mythbuntu-control-centre
6655 ?        S      0:00 gksudo -k -D /usr/share/applications/mythbuntu-contro
6656 ?        Ss     0:02 python /usr/share/mythbuntu-control-centre/bin/mythbu
6721 ?        Z      0:00 [sh] <defunct>
6803 ?        Ssl    0:00 /usr/bin/mythbackend --daemon --logfile /var/log/myth
 

zzz@zzz:~$ sudo pico /tmp/ledxmitd.log

Apr 12 07:27:56 zzz ledxmitd: ledxmitd(serial) ready
Apr 12 07:28:05 zzz ledxmitd: accepted new client on /dev/ledxmitd
Apr 12 07:28:05 zzz ledxmitd: removed client
Apr 12 07:28:06 zzz ledxmitd: accepted new client on /dev/ledxmitd
Apr 12 07:28:06 zzz ledxmitd: removed client
Apr 12 07:28:42 zzz ledxmitd: accepted new client on /dev/ledxmitd
Apr 12 07:28:42 zzz ledxmitd: removed client


anything look wrong here? I've removed a bunch of unrelated stuff from  the ps ax list
thanks

---

### Post by elj4176 on 2008-04-12
I checked the irblaster with winlirc on an xp machine and it lights up if I select 'inverted' and then select 'raw codes'  - it lights up so it does work.
Do I need to change something in the scripts?

$ ps ax | grep lirc
 5245 ?        S      0:00 [lirc_dev]
 5261 ?        Ss     0:00 /usr/sbin/lircd --device=/dev/lirc0
 5715 ?        Ss     0:00 /usr/local/lirc-ledxmit/sbin/ledxmit-ledxmitd -L /tmp/ledxmitd.log


if that helps.I only have 1 com port too.

---

