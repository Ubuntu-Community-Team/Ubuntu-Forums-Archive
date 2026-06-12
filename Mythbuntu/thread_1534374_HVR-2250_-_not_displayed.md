---
title: "HVR-2250 - not displayed"
date: 2010-07-19
forum: Mythbuntu
---

### Post by Barry_IA on 2010-07-19
Hi Folks!

Having a problem with my Backend not displaying my two HVR-2250 tuner cards; the two HVR-1600's work fine.  The left-right arrows at the field to select the capture cards just says the 1600's are already in use.

Have downloaded and installed Steven Toth's drivers.  Well, went through LowSky's instructions and guess they're installed.  Suppose the first thing to do is find out if the drivers are installed properly but no idea how, so wandered around trying to cookbook a solution.  Some attempts below.  (And I know Linux is case-sensitive; I was taught to print in uppercase so my notes are uppercased.  Did enter the commands in the correct case.  My transcribing may have the wrong case.)


$ ls -la /dev/dvb
(response)
Total 0
drwxr-xr-x     4  root        80  2010-07-17 16:10 .
drwxr-xr-x   20  root    4540  2010-07-17 16:10 ..
drwxr-xr-x     2  root      120  2010-07-17 16:10 adapter0
drwxr-xr-x     2  root      120  2010-07-17 16:10 adapter1

I'm guessing that's the two 1600's.



Another thread extract:
Are the HVR-2250 drivers loaded successfully?  Check the output of dmsesg or lspci.  Three million code lines later... <g>  Thank goodness for grep!

dmesg | grep -i 2250      [I'm looking for something listing the HVR-2250 cards]
(result)
14.483808 Code saa7164[0]: subsystem: 0070-88a1  Hauppage HVR-2250 [card=8,autodetected]
14.972773 Code saa7164[1]: subsystem: 0070-8851  Hauppage HVR-2250  [card=7,autodetected]

Well, guess the system is seeing the cards!


What happens with the HVR-1600 cards?
dmesg |grep -i 1600
(reply)
cx-18-0: Autodetected Hauppauge HVR-1600
cx-18-0: Initialized card: Hauppauge HVR-1600
cx-18-1: Autodetected Hauppauge HVR-1600
cx-18-1: Initialized card: Hauppauge HVR-1600

Hmmm: totally different outputs.  Confuse the newbie! <g>



Saw something suggesting
.      modprobe -r saa7164
.      modprobe saa7164 debug=1

With a little bit of trepidation tried that -- seems I recall 'modprobe' can do some strange things, and the 'r' switch was to remove.  Doesn't work right anyway, so.... <deep breath!>
Didn't work -- don't recall the error message.  Tried with saa7164-stable as that is the directory here (following LowSky's instructions); "Not allowed: operation not permitted".  Probably could try sudo but as I don't know what I'm doing anyway, let's not right now!

So, what do I need to do to get the cards displayed so I can configure them?  TIA!

(And a follow-up question is going to be how do I back-up the Operating System so I don't have to go through all this again?!)

---

### Post by LowSky on 2010-07-19
Hi Barry_IA, first things first what verison of Ubuntu are you using?

Are you saying the 2250 are not showing up as possible DVB cards under mythbackend? Is anything listed under DVB?
>  MythTV Instructions

   1. After following the installation instructions at [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200), open MythTV Backend Setup.
   2. Go to capture cards.
   3. Select "New Capture Card".
   4. Set card type to "DVB DTV capture card (v3.x).
   5. The DVB device number will use "adapter0" for the first tuner in the system, "adapter1" for second, etc. This card has two digital tuners so repeat the "New Capture Card" for the next adapter number.

---

### Post by Caysho on 2010-07-20
If everything is set up correctly, you might be seeing [bug #182746]("https://bugs.launchpad.net/bugs/182746")
I have the same card, and need to do a backend restart after every boot.

Do a search in dmesg for DVB, you should see them all.

Mine looks like this:
```

pvruser@pvr:~$ sudo dmesg | grep DVB
[   12.547919] saa7133[0]: subsystem: 1461:2c05, board: AverTV DVB-T 777 [card=85,autodetected]
[   12.548060] input: saa7134 IR (AverTV DVB-T 777) as /devices/pci0000:00/0000:00:1e.0/0000:07:00.0/input/input6
[   12.732201] DVB: registering new adapter (saa7133[0])
[   12.732204] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...
[   21.516124] tveeprom 7-0000: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
[   21.845023] DVB: registering new adapter (saa7164)
[   21.845027] DVB: registering adapter 1 frontend 0 (NXP TDA10048HN DVB-T)...
[   24.481674] DVB: registering new adapter (saa7164)
[   24.481677] DVB: registering adapter 2 frontend 0 (NXP TDA10048HN DVB-T)...

```
The HVR-2200 is driven by saa7164, NXP TDA10048HN DVB-T is the part you are interested in.

Also, run a grep for saa7164_downloadfirmware 

If you are running 10.04, the driver is present and you only need to get the firmware happening - see the [linuxtv hvr-2200 page]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200") for that.

---

### Post by Barry_IA on 2010-07-21
> **LowSky said:**
> Hi Barry_IA, first things first what verison of Ubuntu are you using?

Hi LowSky!

(Hey! If I edit things correctly the quotes display correctly! <gg>  (Referencing message exchange re: *wget -c* in another thread.)

The install-from-scratch version of Mythbuntu 10.04.  Note: 9.10 had been on the computer previously.  Did alter the partition size slightly to force a complete reformatting -- with previous installations seemed like there was data present that shouldn't have been left.  


> **LowSky said:**
> Are you saying the 2250 are not showing up as possible DVB cards under  mythbackend? Is anything listed under DVB?

Right.  Double-checked just now:
  
Select Mythbuntu Control Centre from Desktop
  
System asks for password to kill Backend, then loads MCC; select MyQSL (something like that -- I've a few screens in as I write this.)
   
2 Capture Cards
   
Select (New Capture Card).  At the bottom of that page lists the two HVR-1600 cards currently working.  (I want to install the two HVR-2250's.)
   
Card Type field -->  DVB DTV
   
DVB Device Number --> only toggles between "/dev/dvb/adapter0/frontend0 -- warning already in use" and same thing except is "adapter1".  Attempting to alter this field (delete key, overtype) does not work.  (I remember reading somewhere if the card type doesn't populate to type it in manually -- this did work at one time under 9.10.)

TIA!

S.N. question -- how do we indent/add spaces to the beginning of a line? Originally instead of the blank line between steps had them indented by three spaces.  In another message had attempted to 'outsmart' by putting a period at the beginning of the line and then adding the extra spaces followed by the text.  The extra spaces disappeared!

---

### Post by Barry_IA on 2010-07-21
> **Caysho said:**
> If everything is set up correctly, you might be seeing [bug #182746]("https://bugs.launchpad.net/bugs/182746")
I have the same card, and need to do a backend restart after every boot.

Hi Caysho!

Not sure what that means.  I think I've exited the Backend: system asks for Password before it allows me to enter MCC > MySQL.  IIRC the warning displayed is to shut down the Backend.  As noted in previously reply to LowSky the two HVR-1600 cards are displayed but can't get the two HVR-2250's aren't.



> **Caysho said:**
> 
Do a search in dmesg for DVB, you should see them all.  

Nope. :(  

Originally did *dmesg | grep -i DVB* as reading from printout.  Your *sudo dmseg | grep DVB* was on the next page.  Same results.

My results is as follows (typing by hand so leaving the line numbers out):
DVB: registering new adapter (cx18 )     <laff: need  space between the 8 and right_parens else displays as "(cx18)"!!>

DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)

cx18-0: DVB Frontend registered

cd18-0 registered DVB adapter0 for TS (32 x 32.00 KB)

DVB: registering new adapter (cx18 )

DVB: registering adapter 1 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)

cx18-1: DVB Frontend registered

cx18-1: registered DBV adapter1 fro TS (32 x 32.00 KB)

(Returns to promipt)

Nope, nothing about the 2250 cards.  <sniff>




> **Caysho said:**
>  Also, run a grep for saa7164_downloadfirmware    

dmesg | grep -i saa7164 
Whoa!  Got more than a pageful for saa7164!  (Please don't make me type that! <gg>

..Ah!  highliter on printout confusing me!  * dmesg | grep -i saa7164_downloadfirmware* results in: 

(All lines begin with "saa7164-downloadfireware()")

no first image

waiting for firmware upload (v4l-saa7164.1.0.3-3.fw

Upload failed. (file not found?)



These three lines are repeated a second time.  Only difference appears to be the numbers at the beginning of the lines.  First set start with a 14, second set a 15.  Remainder of the number number different -- I'm thinking the numbers don't have a bearing onthe problem but that lack of an image, etc., certainly does!!




> **Caysho said:**
> If you are running 10.04, the driver is present and you only need to get the firmware happening - see the [linuxtv hvr-2200 page]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200") for that.

Well, quite frankly that was the reason for me putting 9.10 on hold and waiting for 10.04 to come out.  Was under the impression the drivers, etc., needed for the HVR-2250 cards would be automatically installed, could record all of my favorite shows, the boss wouldn't yell at me, I'd win a lottery even though I never enter, I could retire..... but I digress.  <laff>

Will look at the Linux HVR-2200 page later -- I need a break.  (Know there is some relation between the 2200 and the 2250 card I have.)

Thanks for your help!

---

### Post by LowSky on 2010-07-21
Ok I think I have an idea of what the probelm is. The HVR-1600 is a hybrid tuner, it has a digital and should show up listed under DVB DTV cards as well. You should see this unber mythbackend:

```
/dev/dvb/adapter0/frontend0
/dev/dvb/adapter1/frontend0
/dev/dvb/adapter2/frontend0
/dev/dvb/adapter3/frontend0
```

But I have a feeling the firmware wasn't install properly.. 

It might be caused by the newer model of the 2250, maybe this will help

download this file: ```
wget -c http://steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw
```
then save it to the /lib/firmware folder using this command ```
sudo cp *fw /lib/firmware
```

then reboot and try to add the card again under mythbackend


again here is the tutorial I wrote. 
[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)
I think you messed up downloading and installing the firmware. its best to copy and paste the commands to avoid any issues```

```

---

### Post by Barry_IA on 2010-07-21
> **LowSky said:**
> Ok I think I have an idea of what the probelm is. The HVR-1600 is a hybrid tuner, it has a digital and should show up listed under DVB DTV cards as well. You should see this unber mythbackend:

```
/dev/dvb/adapter0/frontend0
/dev/dvb/adapter1/frontend0
/dev/dvb/adapter2/frontend0
/dev/dvb/adapter3/frontend0
```But I have a feeling the firmware wasn't install properly.. 


Hi LowSky!

Uh, no idea how to get to the above.  Tried *mythbackend | grep -i /dev/sbv/adapter* -- didn't get anything like the above but did get a bunch of "failed to open" lines, which I'm guessing would further indicate the installation didn't go as it should have, verifying your 'firmware wasn't installed properly" guess.



> **LowSky said:**
> 
It might be caused by the newer model of the 2250, maybe this will help

download this file: ```
wget -c http://steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw
```then save it to the /lib/firmware folder using this command ```
sudo cp *fw /lib/firmware
```then reboot and try to add the card again under mythbackend  

OK, this one was 'interesting'.  Typed in the *wget -c http:steventoth....*line.  Response: "Network is unreachable."    <grumble>     Double-check entry; Up_arrow to repeat the command.  (long pause)  "Failed.  Connection timed out. retrying."  Allowed to cycle four or five times.  ^C to quit.  Maybe it's "firmware" (singular)?  Up_arrow, backspace to edit out the 's' - nope ==> "404".  Up_arrow, put the 's' back in; connects immediately!  (Did we have to wake up the remote computer? <g>

The 'copy' command - no errors.

Reboot.  This time I exited from Terminal and powered down the computer; usually it's a soft boot (sudo reboot).

Powered up.  (Takes a while -- presume is a good sign!)   Boots to the Frontend (as it is supposed to).  Old recordings still there.  (Good!!)

Exit to desktop; load Terminal.  Try the 'backend' command your gave as the first suggestion -- even with the grep have no real idea what I'm looking for but it does look different.  (Doesn't look at all like your example.)

Try  *dmesg | grep -i dvb*.  Ooo!  Long list!!!  At the top is the data for the two HVR-1600 tuners.  ...Followed by  <drumroll please!!>  "registering new adapter (saa7164)" and lines which include "adapter 2 frontend 0",  "adapter 3 frontend 0",  "adapter 4 frontend 0", and  "adapter 5 frontend 0"!!!  S/b for the two HVR-2250 cards with the dual tuners!!!

Will proceed to install the new capture cards and get back with the results!  (I'm excited!!  Thank you thank you thank you!!!!!!!!)

---

### Post by LowSky on 2010-07-21
your welcome, and good luck... Send me a PM if everything works or you need help on something.

like Caysho said if you turn the computer on or reboot you will need to restart the backend before using the tuners. The problem is that myth starts before the drivers are fully loaded and causes a problem.

there is a work around but it isn't ideal. Personally I dont allow the front end to start automatically and just quickly boot into the backend, exit, saying no to autofilling the database, and starting the frontend.
But this is infrequent, my HTPC is on all 24/7. Heck I can log in from work using teamviewer to run updates or grab needed files offf the machine if needed.

---

### Post by Barry_IA on 2010-07-21
> **LowSky said:**
> your welcome, and good luck... Send me a PM if everything works or you need help on something.

Hi LowSky!

But that would upset everyone reading this thread: did he finally get it going??  Is this the fix to my problem?! <g>

The good news: IT WORKS!!!   Bad News -- not getting all the channels.  Might be a problem with the splitter and/or the coax between the splitter and the tuners -- will check that tomorrow.  (Some details follow.)


> **LowSky said:**
> Like Caysho said if you turn the computer on or reboot you will need to restart the backend before using the tuners. The problem is that myth starts before the drivers are fully loaded and causes a problem.

there is a work around but it isn't ideal. Personally I dont allow the front end to start automatically and just quickly boot into the backend, exit, saying no to autofilling the database, and starting the frontend.
But this is infrequent, my HTPC is on all 24/7. Heck I can log in from work using teamviewer to run updates or grab needed files offf the machine if needed.

I'll have to experiment with that.  If my HVR-2250 tuners suddenly disappear I'll know not to panic and just turn off auto-log-on.  

As I mentioned above, having a problem with the various HVR-2250 cards not detecting all of the channels during #4. Input Connections.  LIS may be a spitter and/or coax problem.

Tuner #0: HVR-1600 #1 
Tuner #1: HVR-1600 #2
Tuner #2: HVR -2250 #1a - Picked up ATSC Ch 4 only (RF 4 -- locally WHBF-DT is on VHF, all the other stations are UHF.)
Tuner #3: HVR-2250 #1b - Picked up ATSC Ch 4 only also.  Starting to panic!
Tuner #4: HVR-2250 #2a - Picked up ATSC Chs 4, 23, 34, 36, 38, 49 -- 14 channels total.  Feeling much better!!
Tuner #5: HVR-2250 #2b - Picked up as above except for Ch 23  - 12 channels total.

Off-hand don't know 'who' Ch 23 is.  Have a chart around here someplace but I'm thinking that problem will go away with the rescan after I get the weak signal problem resolved.  Playing with the new tuners watching Live TV there were a few stations with a bad picture ==> cutting out (pixellation).

Another thing that had me starting to panic was with six tuners still had recoding conflicts!  Apparently something had to update and that took maybe five or ten minutes.  System Info was showing six tuners in Tuner Status.  Log Entries was displaying

Problem with capture cards
No capture cards are defined
Problem with capture cards

Those three lines probably four or five more times before displaying the normal messages about commercials being processed, etc.

Went back and noticed the Upcoming recordings screen now said No Conflicts!  <Happy dance!!><g>

So, 'nuff for tonight!  Will look at the splitter/coax problem tomorrow some time and report in.

---

### Post by LowSky on 2010-07-21
LOL I only wanted a PM just in case things didn't work at all, I pretty good about adding info to the threads.

scan for channels using a cable that hasn't been split 6 times. If you going to split a cable that many times your going to need a amplified spliter.

As for who ch 23 is, where do you live? Go here to find out what channels you should get: [http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/)

---

### Post by Barry_IA on 2010-07-22
> **LowSky said:**
> scan for channels using a cable that hasn't been split 6 times. If you going to split a cable that many times your going to need a amplified spliter.

Hi LowSky!

Just might have to get an amp or amplified splitter.  Replaced the original splitter and coax jumpers this afternoon -- *much* better!!  Had played with three old amplified splitters I had here from previous uses.  Probably ten years old.  One was the same, two were worse (measured using S-meter in a TV Converter for an analog TV).  New connections could use an amplified signal -- any suggestions?  (Antenna is orientated correctly.)



> **LowSky said:**
> As for who ch 23 is, where do you live? Go here to find out what channels you should get: [http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/)

Bookmarked this site - thanks!  Live in Bettendorf, IA (52722).  Five miles upriver from Davenport, IA; across the Mississippi River from Moline, IL, and Rock Island, IL (Quad Cities).  ...RF 23 is WQPT -- odd, it and most of the local stations transmit from the antenna farm in Orion, IL.  RF 4 still transmits from the antenna farm about 4 miles northwest of here (antennae?  we don't need no steenkin' antennae!! <gg>).

---

