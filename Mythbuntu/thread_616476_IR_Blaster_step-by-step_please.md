---
title: "IR Blaster step-by-step please"
date: 2007-11-18
forum: Mythbuntu
---

### Post by Abishye on 2007-11-18
Hardware
Tuner card: Hauppauge WinTV-PVR-150 MCE w/remote; input is composite (from satellite receiver)
Remote: USB IR receiver with 2 transmitter outputs (IR1 and IR2), silver MCE remote;  my blaster is plugged into port IR1 of the transceiver.

Software
Operating System: Ubuntu 7.10 64-bit Desktop (Kernel version: 2.6.22.14-generic)

“dmesg | grep lirc” results in:
[   44.016844] lirc_dev: IR Remote Control driver registered, at major 61
[   44.049804] lirc_mceusb2: Philips eHome USB IR Transciever and
Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $
[   44.049807] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin
Blatter <martin_a_blatter@yahoo.com>
[   44.319991] lirc_dev: lirc_register_plugin: sample_rate: 0
[   44.323831] lirc_mceusb2[3]: Topseed eHome Infrared Transceiver on usb2:3
[   44.323866] usbcore: registered new interface driver lirc_mceusb2


I can record fine, playback is fine, getting my electronic programming guide from Schedules Direct ok.  Sound works, no problems with video.  The “irw” shows the proper buttons are being recognized from the silver remote.  I have read many forums, guides, instructions how to build a serial blaster, etc.  but I’m still not exactly sure to do first to work on the communication from the IR transceiver to the blaster (to the satellite receiver).

I’m putting together a comprehensive set of instructions to share with everyone after this project is complete.  I think the blaster is the last piece.

Just wondering if someone could please tell me in simple terms what I need to do to get the blaster working to change channels on the satellite receiver automatically?

Much thanks.

---

### Post by superm1 on 2007-11-19
There are a few threads in this forum that already discuss this, but I don't know off hand if any go start to finish.

The jist of it for a mceusb2 should be:

1) Find the lircd.conf that represents your satellite remote.

2) Append this lircd.conf to /etc/lirc/lircd.conf

3) Restart Lirc

4) Test out that you can transmit a few buttons
```
irsend -d /dev/lircd SEND_ONCE REMOTE BUTTON
```

5) Download a copy of a channel changer perl, bash, or python script to /usr/local/bin.  Make sure its executable.

6) Modify said script to match your remote name and/or buttons

7) Test sending a channel change with the script at command line.

7) Open mythtv-setup and add your script to the channel changer area for your device.

8) Profit.

---

### Post by OffAxis on 2007-11-19
Just to embellish on a few points from superm1's post...

> 1) Find the lircd.conf that represents your satellite remote.
look here:
[http://lirc.sourceforge.net/remotes/]("http://lirc.sourceforge.net/remotes/")

> 3) Restart Lirc

```
sudo /etc/init.d/lirc restart
```

> 4) Test out that you can transmit a few buttons
Code:

irsend -d /dev/lircd SEND_ONCE REMOTE BUTTON


-d = device
/dev/lircd = the device path (in some cases is lircd0)
SEND_ONCE = send only one signal
REMOTE = the name of the remote (not just 'remote control', but 'remote device' i.e. cable box, sat. box, etc) as labeled in lircd.conf
BUTTON = channel number or a function like POWER (as defined in the remote device's section in lircd.conf)


> 5) Download a copy of a channel changer perl, bash, or python script to /usr/local/bin. Make sure its executable.

Here's a script off superm1 site...

```
#!/usr/bin/perl

# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = "gi-motorola-dct2000";

sub change_channel {
        my($channel_digit) = @_;
        system ("irsend SEND_ONCE $remote_name $channel_digit");
        sleep 1;
}

$channel=$ARGV[0];
sleep 1;
if (length($channel) > 2) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
        change_channel(substr($channel,2,1));
} elsif (length($channel) > 1) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
} else {
        change_channel(substr($channel,0,1));
}
system ("irsend SEND_ONCE $remote_name ENTER");
```
change the** remote_name** to match yours and
name it something like **channel-change.pl**
then
```
sudo chmod +x channel-change.pl
```
and```

cp channel-change.pl /usr/local/bin

```


There's also a write up in the user docs section here:
[https://help.ubuntu.com/community/MythTV_External_Channel_Changer]("https://help.ubuntu.com/community/MythTV_External_Channel_Changer")

---

### Post by Trimble Epic on 2007-11-27
Help!!

I'm sooo close, yet so far...

Ok, I've followed all the instructions to get my haup PVR150's internal blaster working.  It works, I've changed a channel with it.

I've downloaded a channel change script, saved it to usr/local/bin/change-channel.pl and made it executable.  It's working, I've seen it change channels on the Dish Network receiver.

My pvr150 tuner card is working - I can MANUALLY tune in channel 3 and see the output from my Dish network receiver showing up in Myth under Watch TV.

HOWEVER...

When I go into mythtv setup and add the channel change script to the input source, and set initial tuner channel to 3 , it seems that Myth is NOT setting the tuner to 3.  I get static/snow on the screen.  I know the dish is changing channels correctly because I can see the blaster pulsing, and I can connect the output of the dish directly to the TV and see that it's putting out correctly - it just seems like the haup tuner is NOT set to channel 3.  I go back in and remove the channel change script, and then I can once again manually change the channel to 3 in Watch TV and I can see the picture fine.

Sooo...  What causes Myth to fail to set my tuner to channel 3 when I have the channel change script in place?  I'm stumped.

---

### Post by superm1 on 2007-11-27
> **Trimble Epic said:**
> Help!!

I'm sooo close, yet so far...

Ok, I've followed all the instructions to get my haup PVR150's internal blaster working.  It works, I've changed a channel with it.

I've downloaded a channel change script, saved it to usr/local/bin/change-channel.pl and made it executable.  It's working, I've seen it change channels on the Dish Network receiver.

My pvr150 tuner card is working - I can MANUALLY tune in channel 3 and see the output from my Dish network receiver showing up in Myth under Watch TV.

HOWEVER...

When I go into mythtv setup and add the channel change script to the input source, and set initial tuner channel to 3 , it seems that Myth is NOT setting the tuner to 3.  I get static/snow on the screen.  I know the dish is changing channels correctly because I can see the blaster pulsing, and I can connect the output of the dish directly to the TV and see that it's putting out correctly - it just seems like the haup tuner is NOT set to channel 3.  I go back in and remove the channel change script, and then I can once again manually change the channel to 3 in Watch TV and I can see the picture fine.

Sooo...  What causes Myth to fail to set my tuner to channel 3 when I have the channel change script in place?  I'm stumped.

Can you try a composite or s-video input instead.  See if that solves it?

---

### Post by Trimble Epic on 2007-11-27
Yeah, I'll try it...  But I really want this to work with the tuner input (coax) due to the way I have the entertainment system wired.  

The composite output from the dish receiver is going to a 4 way splitter box which feeds into the stereo receiver, which feeds it's output to a VCR that condenses the signal back down to coax to feed into an older tv (which doesn't support composite).  The myth is one of the 4 inputs, the dish's raw signal is another.  I wanted to take the coax from the dish as feed it into the myth so that I don't have to find a way to split the composites from the Dish Network receiver.

Let me again say that IT WORKS - that is, if I remove the channel change script, and the "Preset tuner to channel:" setting, then start live TV and put it on channel 3, then I can see the picture from the dish receiver just fine, and I can change the channels on the dish receiver just fine using it's own remote.  BUT - as soon as I put the channel change script back in ("perl /usr/local/bin/change-channel.pl") then I start getting static again and I can't find a way to force the hauppauge tuner to channel 3, since the presence of an entry in the channel change script box in mythtv-setup seems to tell MythTV not to allow the channel on the Hauppauge to change.

I worked with Alexvd_ and tmg4883 in irc to try to improve my logging, and the dump for that can be found here: [http://paste.ubuntu-nl.org/46008/](http://paste.ubuntu-nl.org/46008/)   the line I find interesting is this one: TVRec(1): HW Tuner: 1->1   Does this mean the hardware tuner is being set to channel 1 instead of 3?  This part seems clear: "External Tuning program exited with no error"

---

### Post by Trimble Epic on 2007-11-27
Well, I tried using the composites, but I didn't have any luck with those, with or without the channel change script.  Perhaps I didn't have the settings right, as I never have used the composite input on my hpPVR150 before.  I tried just connecting the yellow video lead, and I left the audio leads off (I dont have an extra cable for that ATM)... perhaps the 150 card needs to detect a jack inserted into the audio lead for it to try to use that input.

---

### Post by tjanzen on 2007-11-27
Anyone know of another site to check for remotes? My set top box is a Motorolla RG2200, which was taken over from Next Level, but I can't seem to find the appropriate codes to use?

---

### Post by Trimble Epic on 2007-11-27
> **tjanzen said:**
> Anyone know of another site to check for remotes? My set top box is a Motorolla RG2200, which was taken over from Next Level, but I can't seem to find the appropriate codes to use?

Assuming the question is for a hauppauge pvr 150 blaster to simulate the remote of your Motorolla RG2200...

The braindump page has a link to a [lircd.conf file that has EVERY code ]("http://www.blushingpenguin.com/mark/lmilk/lircd.conf")the 150's firmware supports.  he also has a link to a [script that attempts to send every power_on code in the list]("http://www.blushingpenguin.com/mark/lmilk/send_power_new").  My suggesting:  use these two tools to try to find a set of codes that your motorolla responds to.

---

### Post by OffAxis on 2007-11-28
Can you preset to channel 3 without putting in a channel changing script?
Can you preset to any channel?

It seems to me since you're using a set top box (stb) that the hauppauge should act like a dumb terminal and record whatever is coming down the coax, regardless of the channel it's set to (pure speculation). 
There's an option somewhere that allows you to pick 'us-cable, antenna, etc'...
Maybe the incongruity is here.
What do you have it set to?

---

### Post by dannyboy79 on 2007-11-28
if this is a PVR-150, do you have the setting within the input that tells the pvr-350 to stay on channel 3 always? it appears that your channel changing script is trying to tune the card versus tuning the cable box.

---

### Post by newlinux on 2007-11-28
If what dannyboy wrote doesn't work try doing:

```

ivtv-tune -c 3 -d /dev/video0

```
replace /dev/video0 with whatever your video device your tuner is.

---

### Post by EnderWiggens on 2008-02-23
First post all,
I am having the exact same situation and need some help please:
I have everything working perfectly but when I put the channel change script in the input connections area I lose the tuner just like the other chap noted here.

I know the script is working as I can issue the command: 
./ change_channel.pl 555 

and it does change the channel on my Star Choice box  (DSR315) (Code Set Number 106 btw) perfectly.

But when ever I put the channel script in it fails.  I have tried putting in channel 3 for the external preset and tried taking it out.  It does not seem to matter.

Anyone have any idea what I can try next.  I have been working on this for 2 months and am losing faith. 

I have a haup pvp-150 with silver remote and ir blaster and am using Unbuntu 7.10.

I would really appreciate any help. I am so close......

---

### Post by EnderWiggens on 2008-02-24
ok an update:

by using:
ivtv-tune -c 3 -d /dev/video0 

and then bringing up the frontend with the external script specified in the input connections section, it seemed to work once but then only submits single digits to the ir blaster.

Going to fiddle with the script and then try again.  Getting closer but you have to put in the ivtv-tune each time you boot the system.

---

### Post by dannyboy79 on 2008-02-25
i send single digits to my SA3250HD STB using a serial ir-blaster. Here's my channel changing script:

#!/bin/sh
REMOTE_NAME=SAE8000 #note, ensure that the REMOTE_NAME is the same as what you have in your /etc/ledxmitd.conf file
/usr/local/bin/check_stb 1>/dev/null 2>/dev/null || :
for digit in $(echo $1 | sed -e 's/./& /g'); do
/usr/local/lirc-ledxmit/bin/ledxmit-irsend SEND_ONCE $REMOTE_NAME $digit
sleep 0.4  # note, you may have to tweak the interdigit delay up a bit, depending on your DISH receiver model
done
/usr/local/lirc-ledxmit/bin/ledxmit-irsend SEND_ONCE $REMOTE_NAME select

FYI, there's other stuff in this script that you might not need, the one line for check_stb is to make sure that the STB is on before it try's to change the channel and start recording. Also, I am using a seperate instance of lirc, one for receiving and one for sending hence the command being /usr/local/lirc-ledxmit/bin/ledxmit-irsend. I don't really use my Mythtv setup as a frontend too much. I use my xbox and xbmcmythtv to watch my recordings. if I do want to watch livetv, I just use the other stb and tv in the family room that's next to the xbox. I just change the input on the yamaha receiver.

---

### Post by naenyc on 2008-02-26
This seems to be an issue where the: "Preset tuner to channel" isn't working.

After reboot these steps must be taken:

External channel change command: "Blank"
Preset tuner to channel:        3
Starting Channel:               3
Start Mythfrontend.
Reset: External channel change command: "change_chan"

For some odd reason, if I only set "Preset tuner to channel: 3" that isn't sufficient.

The starting channel sets the tuner on my card, "Kworld 110" and when
the "External channel change command" is set back to change_chan, this instructs mythfrontend to ignore tuning the Kworld, but rather only send to the external channel change command.

Of course on reboot, the tuner drifts again and have to start over.

What seems strange is, when I query the database, it is set correctly.

SELECT tunechan FROM cardinput WHERE cardinputid = 2;
+----------+
| tunechan |
+----------+
| 3        |
+----------+

mythtbackend -v channel

2008-02-26 14:32:54.643 Channel(/dev/video0): Input #2: 'Television' schan(14) tun(3) v4l1(NTSC) v4l2(Unknown)
2008-02-26 14:32:54.656 Channel(/dev/video0)::SwitchToInput(in 2, '')

Think I'm onto something, but not sure what.  My intuition is that somehow the database is inconsistent with all of the Mythtv upgrades and/or the Fedora7 to Fedora8 change.

...
Now it is all messed up. It is attempting to send channel frequencies,
rather than channels to change_chan.  Seen this before.

---

### Post by gkby on 2008-02-26
I have the same problem with a Hauppauge PVR 350.  The
"preset tuner to channel" entry has no effect when a channel change
script is specified.  I thought the card was defective with perhaps
a bad coax input, and used the composite input with no problems.

After reading the posts here, I was able to start using the coax
input again, by calling ivtv-tune from the channel change script.

```

if ! test -f /tmp/hwtune; then
    ivtv-tune -c 3 -d /dev/video0
    touch /tmp/hwtune
fi

for digit in $(echo $1 | sed -e 's/./& /g'); do
...
```

Also, I remove the file /tmp/hwtune in /etc/init.d/mythtv-backend,
so that ivtv-tune is called just once after a reboot.
Oddly enough, I had "HW Tuner: 3->3" messages in the 
mythbackend log.  So it seems that mythbackend thought the HW
tuner was set to channel 3, when in reality it was not.

Whatever the problem is, it is quite annoying and not at
all obvious to someone setting up Myth for the first time.

---

### Post by naenyc on 2008-02-26
gkby,

Was attempting the same thing in myth-backend, but being on Fedora, was using tvtime.

Do you know anyway to force it to tune and exit immediately?

By the way, on a different set of forums checking out why the channel change script is supplied frequencies rather than channels.

Some of the bewildering logic involved doing sql lookups and/or modifying the database.

Personally I don't buy it, seems to me that if it was working at one time, it should work again, and in addition, why would a channel changing script ever want frequencies?

Yes, too difficult to mythtv newbies, or even for programmers with 20 years experience.

---

### Post by gkby on 2008-02-26
I'm not sure about tvtime, but ivtv-tune does exactly what you want.
It tunes the card to the specified channel and exits.  It reports the
channel frequency on stdout. If it's not available on Fedora, 
you might be able to build it.  I just downloaded the package with
apt-get on Mythbuntu.

Yes, invoking the channel change script with a frequency was
mind-boggling to me.  Having soldered together an IR blaster, I
wasn't sure whether the problem was in the blaster, the script or
the set-top box (given that the box choked on the long series of
digits.)  It was only after hunting on the Net with the odd strings,
that I figured out they were frequencies.

After realizing that the card's tuner was not being set correctly,
I tried to manually create a separate "channel 3",  hardcoding in 
the frequency of 61.25 MHz.  That seemed to work until the listing
data download, which created the other "channel 3".and torpedoed
this solution.

In any case, the ivtv-tune method works fine.  I'll live with this 
setup until hopefully, the problem is fixed in a future release.

Yes, the pre-packaged Myth distributions have probably come a 
long way with the hard work of many folks, but they aren't yet
plug-and-play.  A basic conifiguration with a Hauppauge card,
TV-out and an IR blaster controlling a set-top box should work
with almost no tweaking.

---

### Post by CleverJake on 2008-05-12
Im really close to having this work, but im not sure where im going wrong

as per the original walkthrough, ive gotten for sure up to step 4 (Test out that you can transmit a few buttons)

```
irsend -d /dev/lircd SEND_ONCE DCT7000 POWER
```

turns my stb on and off

next I downloaded the channel change perl script

```
#!/usr/bin/perl

# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = "DCT700";

sub change_channel {
        my($channel_digit) = @_;
        system ("irsend SEND_ONCE $remote_name $channel_digit");
        sleep 1;
}

$channel=$ARGV[0];
sleep 1;
if (length($channel) > 2) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
        change_channel(substr($channel,2,1));
} elsif (length($channel) > 1) {
        change_channel(substr($channel,0,1));
        change_channel(substr($channel,1,1));
} else {
        change_channel(substr($channel,0,1));
}
system ("irsend SEND_ONCE $remote_name ENTER");
``` 

and saved it to /usr/local/bin/channel-change.pl

Then I go to mythbackend setup, and point the channel change to /usr/local/bin/channel-change.pl

save and exit


but when i go to mythfrontend, the remote doesn't send the signal at all, and acts like it did without the channel script in place


any clue?

thanks guys

---

### Post by BatPenguin on 2008-05-12
> **CleverJake said:**
> Im really close to having this work, but im not sure where im going wrong

Hopping in here since I'm having problems with the PVR-150's blaster and Hardy. Are you using Hardy? If so, I'd love to hear exactly what you've done to make PVR-150's blaster work.

As for suggestions, a couple come to mind:
- did you make sure the script works otherwise? As in, just execute the script yourself and see if it changes the channel? 
- Do you have a default channel to tune set in Myth? I recall this having had some effect as some point with Lirc...don't remember which way (whether it has to be tuneable or blank). Give it a try.

Looking forward to hearing more about your setup...hopefully we can help each other get this going.

---

### Post by wizard10000 on 2008-05-12
I had absolutely no luck getting a serial IR blaster to work with a PVR-150 and a Dish 522/625 box.  I could get the IR blaster to send commands but couldn't find a working lircd.conf that the receiver could understand.

What I ended up doing - which is absolutely no help to you, was setting the channel using ivtv-tune as mentioned above in an init script and setting the default channel change command in mythtv to /bin/true - which does absolutely nothing except return an exit status of 0 so myth would think the channel change had executed successfully.

Then I just manually changed the channel with the Dish remote.  I don't like this solution at all but have had a hell of a time with Dish receivers and IR blasters so I'm gonna subscribe to this thread  :)

---

### Post by BatPenguin on 2008-05-12
Hmm, yeah, I actually do have a working command setup file my digital box (Xsat something or other). Once upon a day when I set that up, I found a file online that pretty much sent every type of command under the sun to the blaster...and I just stared at it for like 20 minutes until something started happening with the box. Then I looked at what the commands did and once I had power on/off and channel numbers, that was it. Did you get this far, sending a ton of commands to see what would work? There was a script file somewhere that I found that was very helpful for this - it really did send like a thousand different things and I just stared at it until something happened.

If any case, I'd love to hear just how you got the blaster to work under Hardy. Did you use a special version of Lirc or just go with the normal ones? And was it i2c module or the lirc_pvr150 you used? Perhaps we can help each other with these different steps.

---

### Post by CleverJake on 2008-05-12
> **BatPenguin said:**
> Hopping in here since I'm having problems with the PVR-150's blaster and Hardy. Are you using Hardy?
Yep

> **BatPenguin said:**
> 
As for suggestions, a couple come to mind:
- did you make sure the script works otherwise? As in, just execute the script yourself and see if it changes the channel?


I dont quite follow. You mean the channel change script?
Thats the bit thats confusing me, its written in perl, and I dont have any experience with perl. Im not sure how to execute that script.

> **BatPenguin said:**
>  
- Do you have a default channel to tune set in Myth? I recall this having had some effect as some point with Lirc...don't remember which way (whether it has to be tuneable or blank). Give it a try.

Yes, I do, turned to channel 3. I can control the channels in the comcast box with the comcast remote, or with single line commands from my terminal, and its a little laggy, but works (I think that may be a low ram issue, but neither time nor place for that)

> **BatPenguin said:**
> 
Looking forward to hearing more about your setup...hopefully we can help each other get this going.

Well Ive got the PVR, and a MCE USB Ir reciever/Blaster combo, running through a brandnew Hardy install with the mythtv thats in the repos (0.21?)

---

### Post by BatPenguin on 2008-05-13
> **CleverJake said:**
> Yep

I dont quite follow. You mean the channel change script?
Thats the bit thats confusing me, its written in perl, and I dont have any experience with perl. Im not sure how to execute that script.


I think it's just 

```
perl /path/script
```

to run a perl script. Make sure it's executable (chmod a+x)

Anyway, sounds like you just have problems finding the proper codes to use. Here's a good page for figuring out the bunch of codesets you can take a look at to see if your box is listed:  

[http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)

If you have the blaster working otherwise, ignore everything else there on that page and head to part 11 "figuring out which codeset to use". There's the test setup that will send all channel change commands etc. so you can see which ones work. Let me know if you have more luck with that, that's how I found out what codes to use.

Well, you're actually not using the PVR-150's own blaster (I have the model with a blaster connection built-in) but a USB one, so your setup won't probably help me. Out of curiosity, how expensive was the USB blaster and where did you get it?

---

### Post by wizard10000 on 2008-05-13
> **BatPenguin said:**
> ...If any case, I'd love to hear just how you got the blaster to work under Hardy. Did you use a special version of Lirc or just go with the normal ones? And was it i2c module or the lirc_pvr150 you used? Perhaps we can help each other with these different steps.

Worked out of the box - but I'm using a serial IR blaster, not the Hauppauge model.  Mine is a white box PVR-150 that didn't come with a blaster so I bought one from another source.

Like I said, I know that doesn't help you a whole lot.  I'm thinking I may just get another card and try it with the Hauppauge blaster as everything on my system works except the channel changer, dammit  :)

---

### Post by BatPenguin on 2008-05-13
> **wizard10000 said:**
> Worked out of the box - but I'm using a serial IR blaster, not the Hauppauge model.  Mine is a white box PVR-150 that didn't come with a blaster so I bought one from another source.

Like I said, I know that doesn't help you a whole lot.  I'm thinking I may just get another card and try it with the Hauppauge blaster as everything on my system works except the channel changer, dammit  :)

Hmm, if you got the IR blaster to send commands, however, like you said before, is the problem just finding the right codes for you? If so (and if you haven't done this already), you might want to check out the link I mentioned in the previous reply to CleverJake. There's a script that will send out all commands possible, maybe that'd help you figure out the codes as well? 

I've been considering buying some USB blaster myself if I can't get this PVR-150 thing to work under Hardy. I just don't really know what to get, I'd of course want something that works with the basic Lirc packages from Hardy.

I'll try once more following the instructions here: [http://www.blushingpenguin.com/mark/blog/?p=24&cp=all#comments](http://www.blushingpenguin.com/mark/blog/?p=24&cp=all#comments)

..and I'll see if I can compile a working lirc_pvr150 module for myself. So far I haven't been able to, the module won't load.

---

### Post by BatPenguin on 2008-05-13
Just a note here that I got my setup working now (Hardy, PVR-150 and its blaster, IVTV version that comes with Hardy). I've described what I did here, in case somebody's interested (now or later):

[http://ubuntuforums.org/showthread.php?p=4949618#post4949618](http://ubuntuforums.org/showthread.php?p=4949618#post4949618)

Hope this helps someone.

---

