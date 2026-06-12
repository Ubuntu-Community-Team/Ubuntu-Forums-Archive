---
title: "Hauppauge Nova-T Remote Control (Kernel Mod)"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by coxy on 2007-06-04
All,
    I intend to get my Hauppauge Nova-T Remote Control (46 button version) working through the Ubuntu kernel specifically through the ir_common module. As it stands only 5 buttons work (Left, Right, Up, Down and Ok) but that is enough to tell me that only an implementation detail is preventing the module from understanding that the other keypresses are supposed to be passed to the application up at the time (Myth TV in this case). I have found the nature of the problem from this [URL.]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_PCI") which suggests that all I need to do is to map the ir codes to keypresses in the module then recompile and voila however when I go to the suggested location >  /usr/src/linux/drivers/media/common/ir-common the ir-common file isn't to be found and when I modinfo the ir_common module it shows it is at > /usr/src/linux/drivers/media/common/ir-common which is essentially the analogous position on the running Kernel and the correct ko file is there. All I would like to know is where I alter the original code to what's below to get my hardware working:

> 
IR_KEYTAB_TYPE ir_codes_hauppauge_new[IR_KEYTAB_SIZE] = {
        [ 0x00 ] = KEY_KP0,             // 0
        [ 0x01 ] = KEY_KP1,             // 1
        [ 0x02 ] = KEY_KP2,             // 2
        [ 0x03 ] = KEY_KP3,             // 3
        [ 0x04 ] = KEY_KP4,             // 4
        [ 0x05 ] = KEY_KP5,             // 5
        [ 0x06 ] = KEY_KP6,             // 6
        [ 0x07 ] = KEY_KP7,             // 7
        [ 0x08 ] = KEY_KP8,             // 8
        [ 0x09 ] = KEY_KP9,             // 9
        [ 0x0a ] = KEY_TEXT,            // keypad asterisk as well
        [ 0x0b ] = KEY_RED,             // red button
        [ 0x0c ] = KEY_RADIO,           // radio
        [ 0x0d ] = KEY_MENU,            // menu
        [ 0x0e ] = KEY_SUBTITLE,        // also the # key
        [ 0x0f ] = KEY_MUTE,            // mute
        [ 0x10 ] = KEY_VOLUMEUP,        // volume +
        [ 0x11 ] = KEY_VOLUMEDOWN,      // volume -
        [ 0x12 ] = KEY_PREVIOUS,        // previous channel
        [ 0x14 ] = KEY_UP,              // up
        [ 0x15 ] = KEY_DOWN,            // down
        [ 0x16 ] = KEY_LEFT,            // left
        [ 0x17 ] = KEY_RIGHT,           // right
        [ 0x18 ] = KEY_VIDEO,           // Videos
        [ 0x19 ] = KEY_AUDIO,           // Music
        [ 0x1a ] = KEY_MHP,             // Pictures - presume this means "Multimedia Home Platform"- no "PICTURES" key in input.h
        [ 0x1b ] = KEY_EPG,             // Guide
        [ 0x1c ] = KEY_TV,              // TV
        [ 0x1e ] = KEY_NEXTSONG,        // skip >|
        [ 0x1f ] = KEY_EXIT,            // back/exit
        [ 0x20 ] = KEY_CHANNELUP,       // channel / program +
        [ 0x21 ] = KEY_CHANNELDOWN,     // channel / program -
        [ 0x22 ] = KEY_CHANNEL,         // source (old black remote)
        [ 0x24 ] = KEY_PREVIOUSSONG,    // replay |<
        [ 0x25 ] = KEY_ENTER,           // OK
        [ 0x26 ] = KEY_SLEEP,           // minimise (old black remote)
        [ 0x29 ] = KEY_BLUE,            // blue key
        [ 0x2e ] = KEY_GREEN,           // green button
        [ 0x30 ] = KEY_PAUSE,           // pause
        [ 0x32 ] = KEY_REWIND,          // backward <<
        [ 0x34 ] = KEY_FASTFORWARD,     // forward >>
        [ 0x35 ] = KEY_PLAY,            // play
        [ 0x36 ] = KEY_STOP,            // stop
        [ 0x37 ] = KEY_RECORD,          // recording
        [ 0x38 ] = KEY_YELLOW,          // yellow key
        [ 0x3b ] = KEY_SELECT,          // top right button
        [ 0x3c ] = KEY_ZOOM,            // full
        [ 0x3d ] = KEY_POWER,           // system power (green button)
};
EXPORT_SYMBOL(ir_codes_hauppauge_new);


If all goes well I would like to suggest the changes are made in the Ubuntu kernel but for the time being I will settle for my Myth TV Box to have a fully supported remote.

Regards
Dave Taylor

P.S. yes I can get LIRC to work but it would be preferable to have ir_common working so that I can have this working by default in future versions of Ubuntu.

---

### Post by dannyboy79 on 2007-06-04
Hi there, I have just recently got my mythtv box working ( i am using Feisty even if my profile doesn't say it). It has an E4300 C2D on a ASRock 775dual-VSTA, 2gb OCZ DDR2 PC6400, 2TB HDD spac, PVR-350 and a BFG 6600 GT OC 128mb GDDR3.

I am currently only using the time warner cable coax cable straight to the PVR-350 until I get my external cable box (so that I can tune to hbo and other premiums that don't come in on the PVR). I have not tried to test the remote for the PVR-350 yet as I just sit in front of my computer (17" HDTV Widescreen is on top shelf and  to the upper right on same desk for watching Mythtv) so I am curious what this is really meaning, ir_common? So you're saying that this is just another way to make your tuner's remote be able to change the channels?

My next question, so you're saying the advantage of the ir_common module working straight away in Ubuntu would be because then if you install Ubuntu Gutsy Gibbon (or whichever one they implement your suggested change into) then you won't have to mess around with LIRC to get the remote to work. 

Maybe a solution for ya? Have you tried to just add that file with the contents you want to that location, then restarting the machine or modprobing ir_common? Just a thought, I am pretty new to linux but I would think that if the module states where it's file for config should be then that's where it shoudl be, and I would chalk it up to a coinsidence that the 4 or 5 buttons work now without the file. What can hurt by putting it there anyway, nothing!

Do you use an external Cable Box? If so, how do you change it's channels? serial, firewire, irblaster? I know ther cable boxs that time warner don't have a serial port that I am aware of, some have firewire (3250HD and 4200HD) and they all have an IR port, I'd like to go firewire as I have heard it's the easiest but I don't know if my cable company has it active. Another weird thing to point out is I don't think I'll be able to record any premium stations thru Firewire so instead of controlling the channels and recording thru firewire, I am just going to chage channels with firewire and record using the PVR-350's composite in. I am certainly going to see if the premium channels are abler to be recorded thru firewire but I doubt. So my question is, are you aware if I can only use the firewire to change the channels and then use the PVR-350 composite in for recording the video input. I do real;ize that the quality won't be near as nice (that's what some1 told me).


I have an off topic question BUT since you're a Mythtv person, I hope you don't mind me asking. I don't reallty want to use Twinview only because I don't see the advantage (for me I am saying) to have my desktop split between the HDTV and my main LCD monitor because of the HDTV's location. (i can't move it, desk prohibits that) So my questions are, how do you watch mythtv on your main computer while you're working? (or maybe you don't)  My backend is also a frontend and I would like to be able to show mythtv output onto the HDTV while I am working on my computer otherwise currently when I start up mythtvfrontend, it opens on my main monitor in full screen, so I can't do any work. I thought about using twinview and just making myth run in a window then dragging teh window over to eh hdtv but that's a total hack job (NOT a good thing, he he) as far as I am concerned. Not to mention, my monitor is at 1280x1024 and hte HDTV native res thru VGA is only 1024x768 so twinview doesn't even work for me, the HDTV cuts off the btotom of my desktop  because it only does 1024x768. So do you have any suggesrtions for me? I would really appreciate it.

Sorry so long, but this whole mythtv thing creates many questions.

---

### Post by coxy on 2007-06-04
Unfortunately the changes that are being made will go in to the ir_common binary file so I will need to know where that is to compile it with the extra detail in before it will work but thanks for the suggestion.

The advantage of ir_common is only really because it will be deprecating the need for lirc in the future I figured I might as well do things properly and go with the new technology.

I don't use an external cable box as I haven't even got a TV license (something that's unique to the UK I think - it basically pays for the BBC).

I also can't help you with Twinview as all I have done is set up an extra machine to display through a regular PAL tv through an S-Video connection. I very much doubt the box is capable of HDTV although that is less of an issue as PAL is somewhat better than NTSC (apart from the reason that all electrical good are way more expensive here than in the states so HD is less of an option until I get a better job or the prices come down - sorry to talk at a tangent there).

Any ideas anyone else?

---

### Post by dannyboy79 on 2007-06-04
well thanks for reponding though. So you don't think that by putting your file there and hten recompiling would work? why don't you look thru the .configure file for ir_common? isn'tthat what's used to compile the module with the new file settings or configurations for button presses?

---

### Post by coxy on 2007-06-04
I have my answer!!!!!!! :D


I have found the module in the headers folder and not in the main kernel, I'm not quite sure yet what the headers file is in relation to the main kernel but I assume it is something that modules can be compiled in so that they interface properly with the kernels ABI without replacing the entire kernel. I'll have to investigate some more but it looks like I am on the right path > (in this case /usr/src/linux-headers-2.6.20-16/include/media/)

Thank you very much for your help \\:D/  \\:D/

---

### Post by coxy on 2007-06-05
You can look at the below link for a dual monitor and tv setup. It is with an ATI card but I am sure you can find a similar thing on Google if you have an Nvidia card.

[http://www.phoronix.net/forums/archive/index.php/t-448.html](http://www.phoronix.net/forums/archive/index.php/t-448.html)

---

