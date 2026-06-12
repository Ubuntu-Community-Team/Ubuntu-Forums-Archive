---
title: "IR blaster endlessly repeats channel - need some expert help"
date: 2010-04-12
forum: Mythbuntu
---

### Post by sbradley07 on 2010-04-12
I cannot figure out what is wrong with my IR blaster set up, and cannot find any reference to a similar problem in the forums.  I'm using a channel-change script with an IR blaster attached to my set top box.  When I change channels with the remote (or when I first go into LiveTV,) the channel number gets transmitted to the set top box, but then it keeps repeating endlessly until I manually stop it.  

I've tried 3 different scripts.  ALL of them work fine from the command line (IRW works fine too).  NONE of them work when MythTV executes the script - they all exhibit the same channel-repeating behavior.  It makes LiveTV unusable. 

I'm running Mythbuntu 9.10 (Myth .22) with a Hauppauge WinTV-HVR-1600 (with remote and USB IR blaster.) 

Until I exit out of LiveTV, the Myth frontend log shows repeating lines of:
2010-04-12 20:06:02.039 [mpeg2video @ 0x4956c0]Missing picture start code
2010-04-12 20:06:02.039 [mpeg2video @ 0x4956c0]Missing picture start code
2010-04-12 20:06:02.039 [mpeg2video @ 0x4956c0]Missing picture start code

Here's the script I am currently using:
```
#!/bin/sh
REMOTE_NAME=DCT2000
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
sleep 0.4 # note, you may have to tweak the interdigit delay up a bit
done
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME OK
```


I've been stuck on this for almost two weeks and would really appreciate some help.  Thanks.

---

### Post by azmyth on 2010-04-13
Try adding an exit 0;

```
#!/bin/sh
REMOTE_NAME=DCT2000
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
sleep 0.4 # note, you may have to tweak the interdigit delay up a bit
done
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME OK

exit 0;

```

---

### Post by sbradley07 on 2010-04-13
I added that last line...same result...channel keeps repeating.

---

### Post by dannyboy79 on 2010-04-13
> **azmyth said:**
> Try adding an exit 0;

```
#!/bin/sh
REMOTE_NAME=DCT2000
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
sleep 0.4 # note, you may have to tweak the interdigit delay up a bit
done
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME OK

exit 0;

```

did you try tweaking the interdigit delay?

---

### Post by azmyth on 2010-04-13
Not sure if it matters but who's the owner of the change channel script.

Also, when it continuously runs will the script show up as a process ps -A | grep script_name

---

### Post by sbradley07 on 2010-04-13
> **dannyboy79 said:**
> did you try tweaking the interdigit delay?
Yes.  It was originally 1 second...I tried a couple of settings between 0.4 and 1, all to no effect.

> Not sure if it matters but who's the owner of the change channel script. 

Here are the permissions:
```
-rwxrwxr-x 1 root root 276 2010-04-13 13:34 channel.sh
```

> Also, when it continuously runs will the script show up as a process ps -A | grep script_name
This is the kind of thing I've been searching for...namely something that would show me what was going on while the channels were repeating.  
And the answer is **YES...the script is executing over and over again.  **

Other than a bug in MythTV, I can't imagine what would cause it to repeatedly execute the script.  Any other information I should be looking at to debug this further?

---

### Post by lmclaren on 2010-04-13
A quick question, if you run the script from the command line does it work correctly or does it repeat? You could add a line to echo the output to a file as well to assist debugging.

A stab in the dark, if it is not repeating if run from the command line, are you repeating because of your irexec file has told to repeat?

LM

I use this to run a batch file once in case you need an example

begin
    remote = mceusb
    prog = irexec
    button = Green
    config = /usr/local/sbin/gdmrestart.sh
    delay = 0
end

---

### Post by sbradley07 on 2010-04-13
The script does not repeat when run from the command line.  I echoed some text from the script to a file, and there's a line in the file for every time the channel repeats...which confirms that the script is getting invoked multiple times.

I'm only 4 weeks new to Mythbuntu, so not sure what you mean by "irexec file."  If you mean the ~/.lircrc file, it looks like:
```
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa 
```

And the ~/.lirc/mythtv file contains all the codes for my remote, like:
```
begin
    remote = DCT2000
    prog = mythtv
    button = MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = DCT2000
    prog = mythtv
    button = EXIT
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = DCT2000
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end
```

I'm not sure what the last part of your post is suggesting that I do.  Can you give me more details?

---

### Post by lmclaren on 2010-04-13
sorry for using the wrong terms, you are correct in guessing that I was refering to the files in ~/.lirc/

Can you show me the bit that calls your channel change script? Which button are you using? In the example I posted you can see where I call external script, my script is called by the irexec file (irexec config is put in the irexec file for neatness but does not have to be!) as I use it outside of mythtv to restart the display manager (relogin) in case my front end hangs.

Sorry if I am over simplifying things, I am not sure of your familarity with lirc.

regards

LM

---

### Post by lmclaren on 2010-04-13
ahhh, just found
[http://www.mythtv.org/wiki/Using_an_IR_Blaster_with_MythTV](http://www.mythtv.org/wiki/Using_an_IR_Blaster_with_MythTV)

I am guessing that you are not editing lirc files but are filling out the values in the gui.

I am no expert with this but I like to break problems down, create a simple script that writes one line to a text file to start with and make sure that works only once. I am guessing that the remote you are using to control is repeating, try controlling from a keyboard and see if that is repeating.

LM

---

### Post by azmyth on 2010-04-14
My backend runs as mythtv and my change channel script is owned and in the mythtv group. Probably not your issue but I'm throwing it out since it works for me. What I would do is I would comment everything out besides the shebang and the exit 0; and see if the script still loops. If no loop, then I'd add in your last irsend. Check for loop. If no loop, add the digit loop in.

```
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
sleep 0.4 # note, you may have to tweak the interdigit delay up a bit
done
```

I suspect this is causing your issue. If so, then you could investigate. I'd also use a digital camera to check that your remote isn't sending out a bunch of signals. Search google for the test I'm talking about.

May also want to check with the ps -A | grep script that it's using the same process id or it'll tell you if you're creating a new process as this will help debug.

---

### Post by sbradley07 on 2010-04-14
LM - yeah i did not edit any files, i just added "/usr/local/bin/channel.sh" to the Input Connections config screen in the Myth backend setup.

AZ - over the past couple of weeks i tried a couple of things with the permissions...and pretty sure setting Owner=mythtv was one of them.  I will try it again.

When I get some time later today, I will try the suggestion to incrementally add lines to the script.  

As for the results of "ps -A | grep channel.sh" and the process ID - - if the proc id is the 4 digit number in front of the script name, I am almost 100% sure there were different proc IDs when I ran it the other day.  Again, I will go back to retest just to be sure.

---

### Post by sbradley07 on 2010-04-14
Update:  I just retested using the ps -A command, and ran it everytime I saw the IR blaster blinking:

```
mythtv7@mythtv7-desktop:/$ ps -A | grep channel.sh
 4925 ?        00:00:00 channel.sh
mythtv7@mythtv7-desktop:/$ ps -A | grep channel.sh
 4943 ?        00:00:00 channel.sh
mythtv7@mythtv7-desktop:/$ ps -A | grep channel.sh
 4964 ?        00:00:00 channel.sh
```

If I read that correctly, different process IDs means the script is not looping, but rather Mythtv is executing it over and over.  

I'd guess that continuing to troubleshoot the script would be a dead-end at this point.  
Any suggestions how I troubleshoot from here?

---

### Post by dannyboy79 on 2010-04-15
here's the script that I used when I had my serial ir blaster connected to a SA-4200HD. not sure if it's any different than what you got.


#!/bin/sh
REMOTE_NAME=SAE8000 #note, ensure that the REMOTE_NAME is the same as what you have in the other conig file
/usr/local/bin/check_stb 1>/dev/null 2>/dev/null || :
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
sleep 0.4
done
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME select

ignore the check_stb line, that was a script used previous to changing channels to see if the set top box was on and if it wasn't it would send the pwr on command. my box would sometimes get shutoff after a update push from time warner.

mine is located within /usr/local/bin/ and here are the permissions:
-rwxr-xr-x 1 root root     454 2009-08-01 09:43 channel_ch.sh

good luck

---

### Post by sbradley07 on 2010-04-16
Thanks for posting your script, but based on the info above, I don't think it's my script.  In fact, I've tried at least 4 different scripts, some shell scripts, some perl scripts.  The result is always the same:  they all work fine from the command line, and they all experience the repeating channels situation when MythTV invokes them.

So I am concluding I do not have a script problem.  The fact that I can  see the script itself is being executed multiple times (because of the separate process IDs), the problem is either a configuration issue or a bug in Mythtv.  

If anyone has any other ideas on how else to isolate this problem, I would greatly appreciate hearing them!

---

### Post by azmyth on 2010-04-17
I would probably try to enter a channel through your remote then I'd unplug your IR receiver to see if this stops the channel change script from looping then this would tell you the IR receiver is sending multiple signals. Have you figured out what signal is being looped? For example, you enter channel 12 and the blaster just keeps looping 1 and 2.

I don't know if it's a bug with Myth as you'd see others including myself with the same issue.

---

### Post by sbradley07 on 2010-04-18
The numbers that are looping is the channel # that Myth enters Watch TV mode with.  It's the channel that it was tuned to the last time I was in Watch TV mode.  

Let's say it was channel 12.  When I enter watch tv mode, the blaster blinks 3 times; "1", "2", "OK"...which is what my script tells it to do.  Then about 2 seconds later, the "1", "2", and "OK" repeats.  And again, and again, and.....until I stop it by hitting the "back arrow" key on my remote.  

At this point, I press channel 28 - - and the same repeating behavior kicks in all over again.  It doesn't matter if it's a 1-, 2-, or 3 digit channel number.  Any number entered into the remote will loop until I stop it.

---

### Post by azmyth on 2010-04-18
Have you checked the mythfrontend and backend logs to see if it gives you any ideas on why myth keeps trying to change the channel?

---

### Post by sbradley07 on 2010-04-20
I have attached my frontend log.  It's a new log...I started the front-end, entered Watch TV, got the repeating channel behavior, changed to another channel, then exited and saved the log.

Also, since I last posted, I changed my config slightly and the behavior is now a little different, so might be a clue to what's going on.  My tuner is set up very similar to what's documented in the mythtv.org "Scheduled Recordings" documentation (not the wiki).  In fact this picture is almost exactly what I have set up (except I have coax cable into the RF[Tuner1] instead of Antenna):

[IMG]http://www.mythtv.org/docs/BlockDiagramofavideocapturedevice.png[/IMG]
[http://www.mythtv.org/docs/mythtv-HOWTO-12.html#ss12.5](http://www.mythtv.org/docs/mythtv-HOWTO-12.html#ss12.5)

The slight change I made was to the order of input connections on my tuner card.  I now have basic cable line connected to the coax port and the digital cable line up connected from the set top box to the s-video port.

Now when I Watch TV, it must always tune in to Tuner 1 (basic cable via direct coax) so it doesn't fire the IR blaster.  When I type in channel 200 for example, it now changes to that channel correctly.  But if I pull up the On Screen Channel Guide and select channel 201 and hit enter, the IR blaster goes back into it's looping behavior.

---

### Post by lmclaren on 2010-04-20
Have you tried changing channels with the keyboard, does it have the same problem?

If you are changing by remote control, what model is it?

LM

---

### Post by sbradley07 on 2010-04-20
I never thought of that...and didn't even know I could change channels with the keyboard.  I will give that a try and post results.

My remote is:
[http://www.mythtv.org/wiki/File:MCE-Remote-2-v1069.jpg](http://www.mythtv.org/wiki/File:MCE-Remote-2-v1069.jpg)

---

