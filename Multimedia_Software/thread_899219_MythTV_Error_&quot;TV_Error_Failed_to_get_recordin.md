---
title: "MythTV Error &quot;TV Error: Failed to get recording show list&quot;"
date: 2008-08-24
forum: Multimedia Software
---

### Post by Sp4rX on 2008-08-24
Hi all,

i recently install Mythtv on my ubuntu system(s) and i can not for the life of me get it to work with my DVB card.

i have installed mythtv on two systems and get the same errors on both. one is a presario laptop and the other, a normal desktop.

im using a Pinnacle 72e USB DVB card and the computers detect the device etc as this shows
> sean@sean-laptop:~$ dmesg | grep -i dvb 
[  232.913015] dvb-usb: found a 'Pinnacle PCTV 72e DVB-T' in cold state, will try to load a firmware 
[  232.978714] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw' 
[  233.362770] dvb-usb: found a 'Pinnacle PCTV 72e DVB-T' in warm state. 
[  233.362862] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer. 
[  233.363124] DVB: registering new adapter (Pinnacle PCTV 72e DVB-T) 
[  233.586391] DVB: registering frontend 0 (DiBcom 7000PC)... 
[  233.764395] dvb-usb: Pinnacle PCTV 72e DVB-T successfully initialized and connected. 
[  233.764641] usbcore: registered new interface driver dvb_usb_dib0700 
sean@sean-laptop:~$ 



however when i try to run mythtv -setup i get the below output from the terminal

> sean@sean-laptop:~$ mythtv -setup 
2008-08-24 15:12:23.011 Using runtime prefix = /usr, libdir = /usr/lib 
2008-08-24 15:12:23.020 XScreenSaver support enabled 
2008-08-24 15:12:23.020 DPMS is active. 
2008-08-24 15:12:23.021 Empty LocalHostName. 
2008-08-24 15:12:23.021 Using localhost value of sean-laptop 
2008-08-24 15:12:23.030 New DB connection, total: 1 
2008-08-24 15:12:23.036 Connected to database 'mythconverg' at host: localhost 
2008-08-24 15:12:23.037 Closing DB connection named 'DBManager0' 
2008-08-24 15:12:23.054 Primary screen 0. 
2008-08-24 15:12:23.055 Connected to database 'mythconverg' at host: localhost 
2008-08-24 15:12:23.056 Using screen 0, 1280x800 at 0,0 
2008-08-24 15:12:23.647 max_width: 1280 max_height: 800 
2008-08-24 15:12:23.676 Primary screen 0. 
2008-08-24 15:12:23.677 Using screen 0, 1280x800 at 0,0 
2008-08-24 15:12:23.680 Switching to square mode (G.A.N.T) 
2008-08-24 15:12:23.715 Using the Qt painter 
mythtv: could not connect to socket 
mythtv: No such file or directory 
2008-08-24 15:12:23.716 lirc_init failed for mythtv, see preceding messages 
2008-08-24 15:12:23.716 JoystickMenuClient Error: Joystick disabled - Failed to read /home/sean/.mythtv/joystickmenurc 
2008-08-24 15:12:24.475 New DB connection, total: 2 
2008-08-24 15:12:24.476 Connected to database 'mythconverg' at host: localhost 
2008-08-24 15:12:24.496 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5) 
2008-08-24 15:12:24.497 Using protocol version 40 
2008-08-24 15:12:24.505 TV Error: Failed to get recording show list 
sean@sean-laptop:~$ 


Any help would be appreciated. go easy on me though. Im really new to all this.

Thanks.

---

### Post by DemonDomen on 2008-11-18
I know that this thread is old, but I had the same problem and fixed it.

You need to configure the tv channel list (make one). That's how I did it.
The command "mythtv" gets you directly into the tv watching screen. I would recommend that you use "mythfrontend".

---

### Post by Sp4rX on 2008-11-20
hey thanks for that.

im sorta over it now after so long but i might try and give it a ago again soon and see if i can fix it up. thanks again.

---

