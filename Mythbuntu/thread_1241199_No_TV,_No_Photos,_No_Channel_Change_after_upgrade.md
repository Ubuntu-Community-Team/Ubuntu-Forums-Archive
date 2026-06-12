---
title: "No TV, No Photos, No Channel Change after upgrade"
date: 2009-08-15
forum: Mythbuntu
---

### Post by emkamau on 2009-08-15
Hi

I'm really stuck with this. I've had a working Myth setup since Ubuntu 8.04 came out. The other day I decided to upgrade my mother board and add a hardisk and memory. After installing the new mobo, disk etc I promptly upgraded from 8.04 to 8.10. Now Myth is completely broken. 

1. I have no live TV. I simply get a blank screen and then return to the Myth main screen. I also cannot watch DVDs. I get kicked back to the Play DVD menu. However, I can watch recordings and videos on the hardisks. Errors when I start myth from the terminal:
```

2009-08-15 17:05:40.310 Connecting to backend server: 10.192.168.60:6543 (try 1 of 5)
2009-08-15 17:05:40.311 Using protocol version 40
2009-08-15 17:05:40.331 TV: Attempting to change from None to WatchingLiveTV
2009-08-15 17:05:40.332 Using protocol version 40
2009-08-15 17:05:45.577 GetEntryAt(-1) failed.
2009-08-15 17:05:45.578 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-08-15 17:05:45.578 TV Error: LiveTV not successfully started
2009-08-15 17:05:45.578 TV Error: LiveTV not successfully started
2009-08-15 17:05:45.645 TV: Deleting TV Chain in destructor

```

2. I can not view my photos in Myth gallery. I get the error "Sorry: No OPenGl support available" I have tried installing anything OpenGL in the repositories, no dice.

3. Myth cannot connect to my transcoding daemon.

4. My directv.pl channel changing script does not work. My mobo did not come with a serial port (I use the serial to USB connection to my Directv D11 set top box). So I have transfered a serial port (connected to mobo header) from another computer to my mythbox. I have also purchased and installed two different serial port PCI cards. Nothing works. I can detect the serial port with the setserial command, but thats all.

5. Because of the no tv and channel changing, myth cannot record anything.

6. Perhaps related to this; my graphics on the computer are screwed up. The display to the TV is larger than the TV and so is cut off on all sides. I'm using the Nvidia 180 drivers i.e the latest and my card is an Nvidia geforce 8400GS 512MB. 
I get these erros ate the terminal.Notice the screen size is 1280x800. I vae set res at 1024x768 in the nVidia setting. So whats up?
```

2009-08-15 17:05:37.249 New DB connection, total: 1
2009-08-15 17:05:37.254 Connected to database 'mythconverg' at host: localhost
2009-08-15 17:05:37.255 Closing DB connection named 'DBManager0'
2009-08-15 17:05:37.366 Primary screen 0.
2009-08-15 17:05:37.366 Connected to database 'mythconverg' at host: localhost
2009-08-15 17:05:37.368 Using screen 0, 1280x800 at 0,0
2009-08-15 17:05:37.579 max_width: 1280 max_height: 800
2009-08-15 17:05:37.597 Primary screen 0.
2009-08-15 17:05:37.597 Using screen 0, 1280x800 at 0,0

```

All the above was working before my upgrades. I last did this over a year ago so I'm casting around for what works. Permissions on my myth folders are  now at 777 and they are owned by the mythtv user.

I'm sure I'm missing something obvious.
Can anybody give me some pointers as to what may be wrong, solutions etc. 
I'm pulling my hair out here! 

Mythtv Box:
MotherBoard: Gigabyte MA770-UD3
GPU: nVidia Corporation GeForce 8400 GS (rev a1)
nVida Accelerated GRaphics driver (version 180)
Ubuntu 8.10 


Directv STB D11: Connected by serial to usb cable
Tuner card: Hauppuage PVR 150.
Remote control works fine.

emk

---

