---
title: "Installing new video card problems"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by The Pinny Parlour on 2006-08-18
Long

Firstly, thank you to those who reply.

I have a ubuntu box happily running dapper for a while now.  I had a s3 savage4 in it.  today I wanted to upgrade the video card to nvidia 7600gs agp.  Started the pc and xserver-xorg has freaked out.  I have attempted to reconfigure using: sudo dpkg-reconfigure xserver-xorg, but when I get to "Please select your desired default color depth in bits", I select the default (24) and bang.  It jumps straight out of xserver-xorg and into the CLI saying:

 "xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf/20060818195139" (<--obviously date and time)
<name>@ubuntu:~$

I have reverted back to the S3 Savage4 and get the same thing now.  

Any help on what to do would be most helpful.

Thanks
Ian

---

### Post by The Pinny Parlour on 2006-08-18
I just found this from user tseliot, and it worked:

<quote>
 Default  Re: Linux guru, please help. "Failed to start the X server"
Quote:
Originally Posted by PandaToledo
"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.200602071512
This just warns you that it's overwriting your xorg.conf. In other words it's not a problem.

Do this:
sudo nano /etc/X11/xorg.conf

then scroll down the file and get to the Section "Device"
and set the driver to "vesa" like in the following example:
Code:

Driver "vesa"


Press:
CTRL+O to save the file (yes, overwrite it)
CTRL+X to exit

then type:
sudo /etc/init.d/gdm stop (or "kdm stop" if you use Kubuntu)
sudo /etc/init.d/gdm start (or "kdm start" if you use Kubuntu)
__________________
UDSF | My Website | My Envy Script | My Blog 
</quote>

Thank you tseliot  :)

---

### Post by tseliot on 2006-08-18
I have deleted your thread in the Desktop support section. Please don't start more than 1 thread for the same problem.

---

### Post by The Pinny Parlour on 2006-08-18
Sorry.  But I needed my instant coffee in a microwave NOW    :)

---

### Post by The Pinny Parlour on 2006-08-18
ok 

Am now doing a clean, fresh install using 6.06.1 and when it goes through the install process I get a error message saying:
"Fail to start the Xserver (your graphical interface) etc".

This is a clean install????

Video card is nvidia 7600GS AGP. 

 Performing dpkg-reconfigure xserver-xorg goes through the process then hits a brick wall at choosing color depth in bits.   the overwriting of a customised configuration file. 
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 

i never had this bullshit during other installs of ubuntu.  

anyone got ANYhelp this time?

Cheers,
Ian

---

### Post by tseliot on 2006-08-18
> **The Pinny Parlour said:**
> ok 

Am now doing a clean, fresh install using 6.06.1 and when it goes through the install process I get a error message saying:
"Fail to start the Xserver (your graphical interface) etc".

This is a clean install????

Video card is nvidia 7600GS AGP. 

 Performing dpkg-reconfigure xserver-xorg goes through the process then hits a brick wall at choosing color depth in bits.   the overwriting of a customised configuration file. 
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 

i never had this bullshit during other installs of ubuntu.  

anyone got ANYhelp this time?

Cheers,
Ian
Ok, let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by The Pinny Parlour on 2006-08-18
Ok thanks for your help.

Firstly, I have to install every time i do something, (fresh install).

have tried the nv and it gets to the "Please select your desired default color depth in bits", then dies into CLI.  Try sudo dpkg-reconfigure xserver-xorg and try vesa, and vga. same thing happens.  Computer is just about to go on a flight out the :-#  window.  

I can't even get the install to finish, driving me mad.  ](*,)

---

### Post by tseliot on 2006-08-18
> **The Pinny Parlour said:**
> Ok thanks for your help.

Firstly, I have to install every time i do something, (fresh install).
You shouldn't

> **The Pinny Parlour said:**
> have tried the nv and it gets to the "Please select your desired default color depth in bits", then dies into CLI.  Try sudo dpkg-reconfigure xserver-xorg and try vesa, and vga. same thing happens.  Computer is just about to go on a flight out the :-#  window.

If that happens, do:
```
sudo nano -w /etc/X11/xorg.conf
```

Get to the Section "Screen":

```
Section "Screen"
    Identifier  	"Screen[0]"
    Device      	"Device[0]"
    Monitor     	"Monitor[0]"
    DefaultDepth    24
...

```

And make sure the DefaultDepth is set to 24.

If that doesn't solve the problem:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and restart the Xserver:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

---

### Post by The Pinny Parlour on 2006-08-18
Thanks for your help.

Loading the install CD, I experimented and selected the second option, then all went fantastically from then on.

---

