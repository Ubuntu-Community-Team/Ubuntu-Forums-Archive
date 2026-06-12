---
title: "ATI Drivers - Desktop full HD, Myth garbage"
date: 2008-11-01
forum: Mythbuntu
---

### Post by Interfac3 on 2008-11-01
I just installed a fresh copy of the newly released 8.10 (i386).
The issue with previous versions was my Radeon 3450 HD vid card, but this new Mythbuntu nicely installed the proprietary drivers, and was even able to switch from VGA output to the HDMI connector.

All is well when it boots, the desktop flashes for several seconds in full HD, but then it switches to myth and myth shows me a garbage screen...

When i do ALT+F4 / TAB / ENTER (to exit Myth) I get back to the desktop which again shows nicely in full HD.

What do I need to do to get Myth to use the same video settings as the desktop?

While we're at it, I was able (in the desktop under settings / audio) to switch to the vid card's HDMI audio output. I opened mplayer and tried playing an MP3, but got no sound. I'm assuming there's more I need to do, especially to get Myth to use the HDMI audio as well...?

I am a total newbie to Myth, any help is greatly appreciated.

---

### Post by Keithamus on 2008-11-01
Interfac3, the fglrx drivers are pretty naff and do all sorts of weird things.

Say you run on a 1024x768 display, then youll need to run mythfrontend like this: "mythfrontend --geometry 1024x767". So basically 1px less than your screen res. Should work fine then.

---

### Post by Interfac3 on 2008-11-01
Ok, I will try that. Since Myth starts automatically, where can I change it so it does that automatically?

Also, the "garbage" suggests to me it's a refresh rate issue, no?


edit:ok, that worked perfectly! Awesome, thank you. So what config file do i change to get this geometry at bootup?

---

### Post by Keithamus on 2008-11-01
Thats a good question. I hunted around alot, but couldnt find anything about where to do this.

---

### Post by Interfac3 on 2008-11-01
I added a line to /etc/mythtv/session-settings

enabled the frontend opts line, and added the "--geometry 1920x1081" (1081 will be fullscreen vs 1079 keeps the task bar visible).

I'm assuming there should be a better way to fix the resolution rather then passing it by command line, so if anyone knows i'm still interested.

---

### Post by Keithamus on 2008-11-01
There is another way to prevent this from happening, which might work better;

Before running mythtv, you can export the variable LIBGL_ALWAYS_INDIRECT to true; so

"export LIBGL_ALWAYS_INDIRECT=true && mythfrontend"

This works better in my experience, as it is still fullscreen so you dont get the taskbar popping up while watching tv. Its a little more fiddly to set up however, the menus in mythbuntu dont seem to like multiple commands, perhaps making a .sh file with that would work though.

---

### Post by Keithamus on 2008-11-01
Just letting you know I set

export LIBGL_ALWAYS_INDIRECT=true

in my /etc/mythtv/session-settings, and it works perfectly, for autostart and menu systems. Its better than using the geometry hack, as changing channels works without screwing up the picture.

Happy viewing, please change the thread to solved if this solves it for you!

---

### Post by JugeHuge on 2008-11-12
> **Keithamus said:**
> Just letting you know I set

export LIBGL_ALWAYS_INDIRECT=true

in my /etc/mythtv/session-settings, and it works perfectly

Whoa.. Where this did came from?? Now my frontend doesn't crash after exiting livetv.. whee.. Thank you..

---

### Post by Tim Pintsch on 2008-11-15
I was experieincing a problem like described with a Gigabyte S-Series Motherboard with onboard ATI, model number GA-MA69VM-S2 to be precise with built-in video

Thanks,

tim.

---

### Post by loneranger on 2008-11-30
hi
thanks for the soultion but i still have the same problem on the backend where do i have to put the licgl command to sort out the scrambled backend

---

### Post by Keithamus on 2008-12-01
loneranger, the /etc/mythtv/session-settings file is called when mythfrontend is run with the --service argument. So try running mythbackend the same way:

```
mythbackend --service
```

If this doesnt work try this:

```
export LIBGL_ALWAYS_INDIRECT=true && mythbackend
```

---

### Post by Afkpuz on 2009-01-05
I had this problem as well using an ati HD3450.  Updating to ati's latest drivers from their website solved it for me

---

### Post by gungfujoe on 2009-01-11
I too solved this problem on an HD3450 (Asus EAH3450) by installing the latest drivers from ATI's website.  They're a month old (December 10), but they're still newer than the ones that are installed through the standard Ubuntu Hardware Drivers interface.

Now, if I could just get audio to go through the HDMI cable...

---

### Post by CarloMagno on 2009-01-11
> **Keithamus said:**
> Just letting you know I set

export LIBGL_ALWAYS_INDIRECT=true

in my /etc/mythtv/session-settings, and it works perfectly, for autostart and menu systems. Its better than using the geometry hack, as changing channels works without screwing up the picture.

Happy viewing, please change the thread to solved if this solves it for you!
Thank You!

That did the trick for me. I was getting crazy trying to figure out why if I launched mythfronted from the console I get no garbage if I had already set the LIBGL option. It seems that the user launching mythfrontend must set this property previously (so it didnt work for me if I used the launch icon in the panel or main menu). But setting the property in session-settings is clean, it works for lanuch pannel, icon and whatever you want, and there is no need to create a separete custom launch script.. What I dont know yet is if this option has a non desired effect in other applications.

---

### Post by Keithamus on 2009-01-11
I'm on the latest drivers, but I still have corruption issues, when changing channel on livetv, to a channel with a different resolution, the picture becomes corrupted, I have to either exit and enter live tv again, or load and close the program guide a few times.

Anyone experience this problem too?

---

### Post by tegel123456789 on 2009-01-12
I also have problem watching LiveTV or recordings with the fglrx driver for 8.10. I get double screens (one picture on top of the other). I have the onboard ATI 3200HD (R780) on a asus M3A-78 MB.

Right now Iam better of with the radeonhd driver. Has anyone tried the r6xx-r7xx development branch and got Xv to work?

/ Anders

---

### Post by ZweeK on 2009-01-14
> **Keithamus said:**
> Just letting you know I set

export LIBGL_ALWAYS_INDIRECT=true

in my /etc/mythtv/session-settings, and it works perfectly, for autostart and menu systems. Its better than using the geometry hack, as changing channels works without screwing up the picture.

Happy viewing, please change the thread to solved if this solves it for you!

I don't see anything with LIBGL_ALWAYS_INDIRECT=true in my session-settings file. Do I just add it anywhere?

---

### Post by JugeHuge on 2009-01-15
> **gungfujoe said:**
> if I could just get audio to go through the HDMI cable...

You could try this: [No sound over HDMI with ga-ma78gm-s2h AMD 780G motherboard]("http://www.gossamer-threads.com/lists/mythtv/users/333112#333112")


> **tegel123456789 said:**
> I get double screens (one picture on top of the other). I have the onboard ATI 3200HD (R780) on a asus M3A-78 MB.

Change different playback profile or deinterlacer.. Ati doesn't like bob

---

### Post by ZweeK on 2009-01-16
> **ZweeK said:**
> I don't see anything with LIBGL_ALWAYS_INDIRECT=true in my session-settings file. Do I just add it anywhere?

I still need help on this...

---

### Post by JugeHuge on 2009-01-16
> **ZweeK said:**
> I don't see anything with LIBGL_ALWAYS_INDIRECT=true in my session-settings file. Do I just add it anywhere?
[QUOTE=ZweeK;6558053]I still need help on this...[/QUOTE]

Just do i.. add it.. :)

---

### Post by B34N on 2009-03-28
> **Keithamus said:**
> Just letting you know I set

export LIBGL_ALWAYS_INDIRECT=true

in my /etc/mythtv/session-settings, and it works perfectly, for autostart and menu systems. Its better than using the geometry hack, as changing channels works without screwing up the picture.


Worked for me!  Now I can see the menu screen.  However, since this is a new install for me, I need to run the setup.  Unfortunately when I run myth-setup I get the jumbled screen again.  Any thoughts?

---

### Post by B34N on 2009-03-28
> **st8ofmi9d said:**
> Unfortunately when I run myth-setup I get the jumbled screen again.  Any thoughts?

Solved!  I used the --geometry 1600x1199 and it worked

---

### Post by Jr. on 2009-05-03
I'm really new to this, but I'm having the same issue... Where do I but this export line?

EDIT: Ok, I found the file and added the line but it wont let me save the file. It says "Can't open file to write"

---

### Post by SteveGodfrey on 2009-05-03
Bring up a terminal and do this.

tv@M:~$ export LIBGL_ALWAYS_INDIRECT=true
tv@M:~$ mythfrontend

It works for me.

---

### Post by Jr. on 2009-05-03
Thanks Steve, it did something but it didn't help my video. It is still choppy and grainy and I still have that black and white bar on top.

---

### Post by SteveGodfrey on 2009-05-03
Are you running Jaunty? I believe the proprietary drivers aren't available for the ATI cards on the new version of gnome. On my system the open source drivers don't work well enough for Myth :-( 

For now I can't use my system as a frontend, looks like I'll be waiting for ATI to update the drivers or roll back to Interpid.....

---

### Post by Jr. on 2009-05-03
Ya I have ati graphics and Jaunty too. My screen losses signal when I try to use proprietary drivers. I'm forced to use the open-source drivers. Is that the issue? Cause I've been working on this for so long that I'm about to throw out my mobo and buy a new one without onboard graphics and get an nvida card. The issue is that the video quality is so bad, I can't even watch it. It is grainy and I'm only getting maybe 10fps. Is there anyway to bump up the refresh rate? That's the biggest issue.

EDIT: I just tried mythdora and I couldn't even get live tv playback... I just bought this [http://www.newegg.com/Product/Product.aspx?Item=N82E16813130182](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130182)... I was having a lot of other issues with my mobo and graphics anyways.

---

### Post by SteveGodfrey on 2009-05-04
My myth system is running on a HP laptop with ATI graphics. Myth ran great on Intrepid (using the above export command) but since upgrading to Jaunty it's not worked. The open source driver gives me a blue rectangle and that's it!

My main PC is also a HP laptop but with Nvidia graphics, everything works a treat on that one. So you've got the right idea ditch ATI and get Nvidia.

I'm not using Myth at the moment because of this, it's a right pain.

---

### Post by Jr. on 2009-05-04
Ya hopefully nvida will do the trick, I'll post again when I get the board and put her in.

---

### Post by Skip Da Shu on 2009-07-02
> **st8ofmi9d said:**
> Solved!  I used the --geometry 1600x1199 and it worked
 Where?

---

### Post by Skip Da Shu on 2009-07-02
I still can't run mythtv because I can't run the backend setup program due to a garbled screen.  Frontend had the same problem but was fixed with adding this
```
export LIBGL_ALWAYS_INDIRECT=true
``` to my /etc/mythtv/session-settings,

How do I get backend to read this file also?

---

### Post by malachi999 on 2009-07-04
> **Interfac3 said:**
> I just installed a fresh copy of the newly released 8.10 (i386).
The issue with previous versions was my Radeon 3450 HD vid card, but this new Mythbuntu nicely installed the proprietary drivers, and was even able to switch from VGA output to the HDMI connector.

All is well when it boots, the desktop flashes for several seconds in full HD, but then it switches to myth and myth shows me a garbage screen...

When i do ALT+F4 / TAB / ENTER (to exit Myth) I get back to the desktop which again shows nicely in full HD.

What do I need to do to get Myth to use the same video settings as the desktop?

While we're at it, I was able (in the desktop under settings / audio) to switch to the vid card's HDMI audio output. I opened mplayer and tried playing an MP3, but got no sound. I'm assuming there's more I need to do, especially to get Myth to use the HDMI audio as well...?

I am a total newbie to Myth, any help is greatly appreciated.

thanks

---

