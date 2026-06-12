---
title: "Mythtv edgy - DVB - How to"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by Dubstar_04 on 2007-03-01
Ok I realise that a number of people are having difficulties installing mythtv, So i have done my best at making a step by step guide, describing how i installed mythtv on my pc. ive used this method 6 times now and it has always worked.  All the information i used is from superm's, and parkers guides so major credit to them.

If this guide helps just one person it will of been worth while. if you have any problems or find a problem let me know.

Make sure you have ALL repos enabled.

Install video drivers

 I use Envy as it does all the hard work for you. it will install itself too. click the link.

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb)

Envy now has an auto installer and can be run from applications>system tools>Envy


Install tv card drivers (DVB)

Check /dev/dvb/adapter0/ . If the location doesn't exist you will need to install the V4L DVB Drivers, this is done as follows:

```
sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
```

```
hg clone http://linuxtv.org/hg/v4l-dvb 
```


```
  cd v4l-dvb 
```

```
 sudo make 
```

```
 sudo make install 
```

At this point I always take the time to reboot

```
 sudo reboot 
```

You now may need to insert the correct modules for your card however this is done automatically on some cards and with newer kernal.

I have a hauppauge HVR 1300 which uses the cx88 chip. I find this as follows

```
 lspci 
```

```
00:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:07.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
00:07.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05) 
```

you can find more info on your card at:

 [http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

Now you need to add any modules required by you card. this is done as follows:

```
 sudo modprobe cx88-dvb 
```

Other cards are installed just as easy i believe you just substitute the cx88 for your card type for example:

```
 sudo modprobe saa****-dvb 
``` 

note; the driver name isn't always exactly the same as the chip name, and it can be known that nore than just the card driver is needed, for example some cards need dvb_core. 

I also have a pinnacle 310i than when modprobed with saa7134-dvb the /dev/dvb/ folder is populated but the card still doesn't work, therefore requires more research.

You may need to add the module to the modules list if it is not loaded at boot time.

```
 sudo nano /etc/modules 
```

and add your module to the list eg cx88-dvb

Install mythtv

```
 sudo apt-get update 
```
```
 sudo apt-get install mysql-server 
```
```
 sudo apt-get install mythtv mythtv-themes 
```
It will ask you for the root database password. Hit enter if you haven't changed it.
The installation will have created a mythtv user so set the password:

```
 sudo passwd mythtv 
```

You also need to grant access to the mythtv user this is done by adding the user to all the groups that your standard user is added to, do this by adding 'mythtv'
to all the groups in;

```
 sudo nano /etc/group 
``` 

Log out and log back in as mythtv

Setup mythtv

```
 mythtv-setup 
```

Once up have completed the setup process you will receive an error message asking if you want to continue, it reads /var/blah/blah does not exist do you wish to continue?

Click yes, then be sure to run;

```
 sudo /etc/cron.daily/mythtv-backend 
```

This will fill the guide with data.

What now?
At this point it is always a good idea to run 'mythfrontend' and have a quick go with the tv, change channels and maybe record a little. or whatever takes your fancy. To start mythfrontend either select it from the applications > sound and video. Or type mythfrontend into terminal.

Autoload  mythtv?
Easy. when in your gnome desktop goto system > sessions, and add mythfrontend to the start up tab. Done.
You may wish to reboot and test your new settings . 

Auto login?
```
  sudo nano /etc/gdm/gdm.conf-custom 
```

Add the following under the daemon heading;
```
 
[daemon]
AutomaticLogin=mythtv
AutomaticLoginEnable=true
TimedLoginEnable=true
TimedLogin=mythtv
TimedLoginDelay=5

```

Finally add the mythplugins;
```
 sudo apt-get install mythplugins 
```

Combine mythtv controls and Xine (requires a complete lircrc file in /.mythtv)

```
 $ cd
$ ln -s .mythtv/lircrc .lircrc
```

If you have any problems with either mytharchive or ripping dvds double check the location specified in the mythfrontend setup, as it is always the cause of my problems.

---

