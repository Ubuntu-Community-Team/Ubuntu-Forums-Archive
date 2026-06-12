---
title: "Digital Picture Frame as Auxiliary Status Display?"
date: 2008-03-31
forum: Mythbuntu
---

### Post by bt101 on 2008-03-31
Hi - I don't know where to post this, so I'll start here.
I built an Ubuntu htpc (BTW - I ended up using the desktop instead of Mythtv).

Anyway, I would like to setup some sort of auxiliary display so I don't have to turn-on the TV to see status information such as:
-music track info
-a message to indicate that the pc is recording video
-etc

Naturally, I want something cheap and simple.

I looked at 2 line USB displays etc, and rejected them because they are too small to see.

I was wondering if I can use a digital picture frame to display info via USB?  I have never had a digital picture frame.  Does anybody know if these frames will accept a picture via USB for immediate display?

As I would only send very infrequent information to the display, I was thinking a picture frame would work well.

Also, if anybody else has any other ideas that are cheap and simple, please let me know.

Thanks

---

### Post by tgalati4 on 2008-04-01
There are several things you could do:

Buy a cheap 15" LCD display and hang it somewhere useful.  It's low power and you can set visualizations and your desktop to display information, as well as a slide show.

You could write a script to take a screenshot every so often.  These files would get dumped to a mounted directory of your 8" picture frame.  The picture frame would then display the image.  You would have to set the timing of the snapshots to be useful.  In xmms/audacious, there is a plug-in for running scripts before and after a song plays.  This would be a useful place to put the screen snapshot script.

There are several more useful VFD (vacuum flourescent displays) that are larger, but drivers for linux tend to be lacking.  They are popular for gaming servers, but they are not easy to program under linux.

Get a headrest video panel that takes composite video input and split the display with the TV.  You could wire up a push button in a convenient location to turn it on and off.  They are small enough that you can embed the display into an entertainment wall unit.

Set up a laptop (perhaps eeePC) on a small table and ssh into the machine and have it display your desktop for that machine.

Use festival to announce music tracks and recording status.  No need for a display if your computer yaps at you.

There are scripts to light up keyboard LED's so you can program them to indicate recording.  There are plans on the web for using your parallel port (or serial port) to light several LED's depending on system state.

---

### Post by bt101 on 2008-04-01
Thanks, that gives a lot of options.
I did want to try and avoid adding extra video cards and full blown monitors, laptops, etc.
The simplest (and cheapest) does look to be the picture frame (if it works).

As I've never had experience with these frames, I am concerned that I'll go through several of them before I find one that accepts an uploaded picture.  Do all picure frames allow you to mount an upload directory, or is their a partiular model that does this?

---

### Post by tgm4883 on 2008-04-01
I too do not know much about the frames, but the mounting that was mentioned was the mounting of the frame's drive on the computer.

Basically, what you want is the frame to show up as a usb storage device when you plug it in.  I'm not sure this is possible as all the frames I have seen need a memory card plugged into them.  IE, they don't directly hook up to the computer.

Then, the best option would be to write a small program that would grab the info from the xml page, and generate a picture out of it on the mounted drive.

Then you would need some sort of cleanup method that would delete the old photos allowing only 1 photo on the drive at a time.

---

### Post by johnnybirdman on 2008-04-01
> **bt101 said:**
> Thanks, that gives a lot of options.
I did want to try and avoid adding extra video cards and full blown monitors, laptops, etc.
The simplest (and cheapest) does look to be the picture frame (if it works).

As I've never had experience with these frames, I am concerned that I'll go through several of them before I find one that accepts an uploaded picture.  Do all picure frames allow you to mount an upload directory, or is their a partiular model that does this?

I got a nice Kodak frame for my parents for Christmas.  It was easy to hook up and show photos.  Problem you will run into is that when it is connected, much like digital cameras, it doesn't show photo's, it only shows that it is 'connected.'  therefore your script would have to continue to mount/unmount the frame each time you wanted to view, and once unmounted, the model I had didn't exactly reboot quickly.
Just some of my experience, other models may be different.

Good post though. I'm in the process of setting up my mythbuntu box and this would/will be an issue for me as well.  I think, if possible, i'm going to try VNC from another pc or mount a small lcd on the underside of my fliptop a/v rack.
J.

---

### Post by bt101 on 2008-04-01
> **johnnybirdman said:**
> I got a nice Kodak frame for my parents for Christmas.  It was easy to hook up and show photos.  Problem you will run into is that when it is connected, much like digital cameras, it doesn't show photo's, it only shows that it is 'connected.'  therefore your script would have to continue to mount/unmount the frame each time you wanted to view, and once unmounted, the model I had didn't exactly reboot quickly.
Just some of my experience, other models may be different.

Good post though. I'm in the process of setting up my mythbuntu box and this would/will be an issue for me as well.  I think, if possible, i'm going to try VNC from another pc or mount a small lcd on the underside of my fliptop a/v rack.
J.

Thanks for that info.  That's the kind of hiccup of which I was afraid.
I should hold-off on the picture frame thing until I can find one that definitely display an uploaded image.

If anybody knows of a model, please let us know.

The more I think of it, I can see a lot of uses for such an auxiliary display.  When you think of the complex tasks that a cheap $50 picture frame already does, displaying an uploaded image would be a simple software addition.  Manufacturers could have a whole new market where people use these displays not only for htpcs, but for desktops as well (displaying images, email alerts, status info, etc, etc).

---

### Post by johnnybirdman on 2008-04-05
Now that I actually have a functioning Mythbuntu 8.04 setup (how easy it was is just nuts) I need to get something that looks better and will get the PC case off my floor.  I'm looking at HTPC cases and found some with touchscreens in them.  That might be the answer to your issue.  Either internal or external should work.
This one at newegg is just an example **[COLOR="DarkOrange"][http://www.newegg.com/Product/Product.aspx?Item=N82E16811235008]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811235008")[/COLOR]**
I wonder if mythbuntu has the drivers for this and if it, or any, would work??
J.

Or for what you would spend on a frame, go with something like this.
[**[COLOR="DarkOrange"]http://cgi.ebay.com/ebaymotors/294-NEW-7-TFT-LCD-TOUCH-SCREEN-PC-VGA-MONITOR_W0QQitemZ290219793458QQcmdZViewItem[/COLOR]**]("http://cgi.ebay.com/ebaymotors/294-NEW-7-TFT-LCD-TOUCH-SCREEN-PC-VGA-MONITOR_W0QQitemZ290219793458QQcmdZViewItem")
just a small monitor really

---

