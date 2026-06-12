---
title: "Firewire from Step One"
date: 2008-02-25
forum: Mythbuntu
---

### Post by dsbw on 2008-02-25
Is it still required to do [all these steps ]("https://help.ubuntu.com/community/MythTV_Firewire?highlight=%28firewire%29")for firewire recording/viewing?

First things first, though, how do I know the firewire port on the STB is active? I've run plugreport with both ports on the STB and they both return the same values, indicating they're active. Is that all it is, or can this turn up okay and *not* be active port(s)?

I ask because when I follow through on the setup, I don't see the firewire tuner while waatching TV.

---

### Post by volkswagner on 2008-02-25
I have heard plug report is not definitive.  It is best if you can get firewire_tester working.  What cable box do you have?  I recommend following Mythtv firewire how to.  I did not spend any time on the test.mpg portion.  I feel if you get solid results with p2p is good enough.  Check my last thread "more tuners more headaches".  Newlinux offered great tips.

---

### Post by 4dognight on 2008-02-25
I have been going through that same how to. It is fairly complete, but I ran into a few other problems. One thing to watch out for is the node your stb is on. It can change every time you reboot or unplug your firewire. Another problem is if you tune to a channel that doesn't have a valid signal, it drops you out of your firewire tuner in myth. THen, you have to go into the config and change the start channel to something you know works. ( I beleive this to be a bug. Myth shouldnt update your last channel viewed unless it was succesful)

If you have a motorola stb you can get into the diagnostic menu by powering off the stb, then immediately press the select button. Look in D11 for the 5c encryption and whether firewire is enabled. It will also show you your current connections. You will see your PC firewire controller in the list if its working. Also look in D6 for the current channell status. Mine would show COPY FREE if it was available.

you will also want to get the 6200ch channel changer program for firewire connection. I had to enter my vendor ID in the pgm(hard coded), but it worked once i did that.

Another usefule tool i downloaded was one called gscanbus. It is a graphical view of your firewire connections. 

Newlinux useron this forum is very helpful in setting this up. I prob would have given up if it wasn't for his help. 

I still have a problem with my sound but I dont think its firewire related.

---

### Post by dsbw on 2008-02-25
Oh, no! Not NewLinux!

Heh. He's been helping me over in the mythtvtalk forum. I thought I'd give him a break by asking here.:lolflag:

I haven't been able to make firewire_tester work. :(

And I haven't figured out how to get mpeg2-test installedl. (For the record, I think the firewire tools should be part of the mythbuntu installation.) I'd hoped mpeg2-test would come with firewire_tester but no dice.

---

### Post by dsbw on 2008-02-25
Oh, I have a SA 4250HDC.

---

### Post by 4dognight on 2008-02-25
I dont know what the SA STB has for diagnostics. 
As for firewire testerI beleive the same goes for the channel its on. It has to be on a valid channel. If its not on a channel that can be displayed firewire_tester,will just hang and sit there looking back at you. Or at least it did for me. I would use the diagnostics menu first to see if it was available, then try firewire tester.

 I would like to see both firewire tester and especially Myth, figure out which node is the STB automagically, so you dont have to worry which node its using. I would think it cant be too difficult. I noticed when using gscanbus, it displays the ROM  info for each node. In there is the name of each node. In my case it was Motorola for the STB and Linux for my firewire card.

---

### Post by newlinux on 2008-02-25
> **dsbw said:**
> Oh, no! Not NewLinux!

Heh. He's been helping me over in the mythtvtalk forum. I thought I'd give him a break by asking here.:lolflag:



I'm happy to help wherever. This is my way of giving back... Ask away and I'll help when I have time and have ideas. Without the help from these forums I wouldn't have gotten to where I am at. I use myth (and linux) pretty much everyday and it has added plenty of enjoyment to our lives and saved money at the same time...

---

### Post by newlinux on 2008-02-25
> **dsbw said:**
> 
I haven't been able to make firewire_tester work. :(

And I haven't figured out how to get mpeg2-test installedl. (For the record, I think the firewire tools should be part of the mythbuntu installation.) I'd hoped mpeg2-test would come with firewire_tester but no dice.

What problems are you having with firewire_tester and test-mpeg2?

---

### Post by volkswagner on 2008-02-25
> I haven't been able to make firewire_tester work.

Do you mean connection failed or it wont run.  Have you tried p2p and broadcast?

Have you tried removing the firewire cable and running plugreport? Then reinstall fiewire cable, rerun plugreport?  Try the above with both ports, following with firewire_tester.

I seemed to have luck changing port on my box, only one was active.  Also changing channels and running FWtester.  You should also try to make sure you have the latest version of firewire_tester.  In the config file make sure it include the bus reset command as an option -R.  If it doesn't you don't have the latest version.  You can get it here

[http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib]("http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib")

I think the newer version made a big difference for me.

---

### Post by majoridiot on 2008-02-26
> **volkswagner said:**
> I seemed to have luck changing port on my box... You can get it here... I think the newer version made a big difference for me.

the guide has been updated with that link. ;)

> **dsbw said:**
> Is it still required to do [all these steps ]("https://help.ubuntu.com/community/MythTV_Firewire?highlight=%28firewire%29")for firewire recording/viewing?

yup... pretty much.  once you know what's what, you can skip around, but the guide was
written to start from square one and  be as thorough, educational and accurate as possible.

> **dsbw said:**
> First things first, though, how do I know the firewire port on the STB is active? I've run plugreport with both ports on the STB and they both return the same values, indicating they're active.

i recently ran into this while helping someone with their SA4250HD.  both ports do show as active.
the way to tell which is *truly* active is to try and prime them.  one will prime and one will
not.  FYI that box seems to run best on a p2p connection.

for best results, follow the guide from the beginning.  when you get to the priming section,
run mytv-setup first and make sure the stb is set to a channel with no encryption- like a local.
then try priming it- if it fails, switch the firewire cable to the other port on the stb, and check to
see if it switched nodes.

if it did switch nodes, resetting the bus with -R option of firewire_tester may fix
it... if not, just reboot the computer.

once it's back on node 1 (which is where the SA4250 "normally" resides in my experience)
try priming it again.  if neither port will prime and the channel is 5c=0 and cci=0x00, then the
firewire on the stb is not fully enabled and functional.

---

### Post by dsbw on 2008-02-26
> **volkswagner said:**
> Do you mean connection failed or it wont run.  Have you tried p2p and broadcast?

A little of both. :-) First it ran but failed, then I couldn't get it to run. I realized (correctly) at that point that I was getting a little punchy. Got it running, still fails.

> **volkswagner said:**
> Have you tried removing the firewire cable and running plugreport? Then reinstall fiewire cable, rerun plugreport?  Try the above with both ports, following with firewire_tester.

Hey! I got a positive report back from firewire_tester! Yay, me!

> **volkswagner said:**
> I seemed to have luck changing port on my box, only one was active.  Also changing channels and running FWtester.  You should also try to make sure you have the latest version of firewire_tester.  In the config file make sure it include the bus reset command as an option -R.  If it doesn't you don't have the latest version.  You can get it here

I tried this but for some reason wget is giving me the actual HTML. I don't understand; it worked before. (I've had this problem before, I'm pretty sure as a result of doing something really stupid, but I can't recall what it was.)

> **volkswagner said:**
> I think the newer version made a big difference for me.

Well, with luck, I won't need it. (Though anyone who wants to point out what I did wrong on the wget is welcome....)

---

### Post by dsbw on 2008-02-26
> **4dognight said:**
> It has to be on a valid channel. If its not on a channel that can be displayed firewire_tester,will just hang and sit there looking back at you. Or at least it did for me. I would use the diagnostics menu first to see if it was available, then try firewire tester.

Good tip. Thanks. I was beginning to think the hanging was progress.

---

### Post by dsbw on 2008-02-26
> **newlinux said:**
> What problems are you having with firewire_tester and test-mpeg2?

Thanks for the help (again). 

My firewire_tester problem is largely psychological. I seem to be over it for now.

test_mpeg2 on the other hand, I can't find. I thought it would be in my lieb* examples directory but I don't see it. I don't immediately see how to download it either.

---

### Post by newlinux on 2008-02-26
I got mine a long time ago... believe I downloaded and compiled it.

[http://www.linux1394.org/dl/libiec61883-1.1.0.tar.gz](http://www.linux1394.org/dl/libiec61883-1.1.0.tar.gz)

Source code should be in the examples dir...

---

### Post by dsbw on 2008-02-26
> **majoridiot said:**
> once it's back on node 1 (which is where the SA4250 "normally" resides in my experience)try priming it again.  if neither port will prime and the channel is 5c=0 and cci=0x00, then thefirewire on the stb is not fully enabled and functional.

Well, I'm getting sucess doing the P2P testing but no joy on the actual viewing. 

If I try to "Y" to it whle in watching TV mode, it never comes up as an option.

If someone comes up with an test-mpeg2 link for me, I guess that's next....

---

### Post by dsbw on 2008-02-26
> **newlinux said:**
> I got mine a long time ago... believe I downloaded and compiled it.

[http://www.linux1394.org/dl/libiec61883-1.1.0.tar.gz](http://www.linux1394.org/dl/libiec61883-1.1.0.tar.gz)

Source code should be in the examples dir...

Ahhh. thanks. Let's see what happens.

---

### Post by dsbw on 2008-02-26
OK, I got test-mpeg2 downloaded and compiled.

A test-mpeg2 capture shows recorded video from a non-scrambled channel.

Now, "Watch TV" in MythTV shows me pink/white crosshatching and no interface. I have to Esc out.

Progress, of a sort.

---

### Post by newlinux on 2008-02-27
Well, if test-mpeg2 works then you should be able to get it to work.
Sorry if this has been answered, but how many tuners do you have? Are you sure your firewire tuner is available (check system status or mythweb backend status). What do your logs say when trying to watch a firewire station?

Perhaps just for our sake tell us your exact Firewire setup settings in mythtv-setup.

---

### Post by majoridiot on 2008-02-27
> **dsbw said:**
> Now, "Watch TV" in MythTV shows me pink/white crosshatching and no interface. I have to Esc out

are you using the nvidia driver?  if so, there is a known "pink screen" issue.  check out this thread:

[http://ubuntuforums.org/showthread.php?t=638191](http://ubuntuforums.org/showthread.php?t=638191)

and more info on the mythtv mailing list.  changing the driver seems to fix things.

---

### Post by dsbw on 2008-02-27
> **newlinux said:**
> I got mine a long time ago... believe I downloaded and compiled it.

[http://www.linux1394.org/dl/libiec61883-1.1.0.tar.gz](http://www.linux1394.org/dl/libiec61883-1.1.0.tar.gz)

Source code should be in the examples dir...

Hey...I downloaded from there and didn't find a firewire_tester, just a plugreport and a test-mpeg2....

EDIT....Oh, because that was a link to mpeg-test2. Never mind.

OK, the port seems to have gone back to sleep again. It "awoke" yesterday when I switched from one port to the other. Now both seem to be asleep. I'm trying to remember if I did something to wake it up. I could use that firewire_tester.c with the -R option, I guess....

---

### Post by dsbw on 2008-02-27
> **majoridiot said:**
> are you using the nvidia driver?  if so, there is a known "pink screen" issue.  check out this thread:

[http://ubuntuforums.org/showthread.php?t=638191](http://ubuntuforums.org/showthread.php?t=638191)

and more info on the mythtv mailing list.  changing the driver seems to fix things.

Yeah, that looks right. The port's gone back to sleep though so I'm back a step....

---

### Post by newlinux on 2008-02-27
> **dsbw said:**
> Hey...I downloaded from there and didn't find a firewire_tester, just a plugreport and a test-mpeg2....

Yeah, plugreport can be installed from the repos, and firewire_tester is downloaded from somewhere else as detailed in the ubuntu mythtv documentation referred to earlier in this thread...

([https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire))

---

### Post by dsbw on 2008-03-01
OK, so now I've got the firewire responding consistently.

I can capture MPEG-2. I replaced the NV drivers.

But now, the Firewire option just doesn't show up when I'm watching TV. If I delete everything and just put in the Firewire, when I go watch TV, it says all the encoders are in use. 

If I add others in, they show up, but the Firewire doesn't. I don't get it. If I've got the capture/video/input thing all set up, it should show up as an option when watching TV right? Even if it doesn't work?

I mean I can set up a card I don't have and connect it to whatever and it will show up (as static) when I switch TV inputs. But no firewire inputs are showing up!:confused:

---

### Post by majoridiot on 2008-03-01
> **dsbw said:**
> OK, so now I've got the firewire responding consistently.

I can capture MPEG-2. I replaced the NV drivers.

But now, the Firewire option just doesn't show up when I'm watching TV. If I delete everything and just put in the Firewire, when I go watch TV, it says all the encoders are in use. 

If I add others in, they show up, but the Firewire doesn't. I don't get it. If I've got the capture/video/input thing all set up, it should show up as an option when watching TV right? Even if it doesn't work?

I mean I can set up a card I don't have and connect it to whatever and it will show up (as static) when I switch TV inputs. But no firewire inputs are showing up!:confused:

did you addd firewire as a "tuner" in mythtv-setup, select the right stb for it and connect it to a tv line-up like you do for
other tuners?  you know... this whole process is a LOT easier if you just RTFM and follow it!  it was written to alleviate threads 
like this where people refuse to follow instructions. :confused:

SERIOUSLY... follow the guide.  it sounds like your cable box will work ok- so just follow the instructions and you will find that 99% of your problems will be solved, most likely.

[https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire)

no kidding-

[https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire)

---

### Post by dsbw on 2008-03-01
*did you addd firewire as a "tuner" in mythtv-setup, select the right stb for it and connect it to a tv line-up like you do forother tuners? *

Yes! Hence my confusion! I can set up tuner->source->input connections till the freakin' cows come home and any non-firewire (now matter how incorrect) shows up when I try to watch TV but no firewire one does. This has been happening since I replaced the NVidia driver, but I'm not sure how that could be the problem.

I mean, I though I understood the basic setup: If I fill in steps 2, 3 and 4 (in Myth Setup), I'll get a TV input. It may not work, but that's a separate issue. It should be there!

*you know... this whole process is a LOT easier if you just RTFM and follow it! it was written to alleviate threads like this where people refuse to follow instructions. *

Dude, I almost have that thing memorized. I haven't done tne Init Script/Primer stuff because that doesn't seem to be the problem. But maybe it is part of the problem since the port seems to wake up at random and go to sleep whenever it's left alone. I still think that I should be able to see the firewire input when I go into the Watch TV option. (No?)

Believe me, if I could work this out without ever asking a question, I would.

---

### Post by volkswagner on 2008-03-01
My Nvidia drivers broke a working tv card setup.  I had a Kworld 110 setup and functional, channel changing the whole nine.  When I installed the latest Nvidia drivers via Envy, I get a black screen when trying to watch live tv.  I am in the process of trying to get my old drivers working again.

---

### Post by dsbw on 2008-03-01
OK, I've started from scratch (because I really want to understand what's going on, not just punch buttons until something works). Also, setting up MythTV seems to be pretty easy once you figure out what corners you have to piss in, it's just finding those corners out first.

On a brand new installation:

1. For global back end I change the Channel frequence table to us-cable.
2. I go to capture card setup.
   a. I select FireWire cable box
   b. Cable box model SA4200HD
   c. Connection Type: Point to Point
   d. IE-1394 Port: 0
   e. Node: 1
   f. Speed 100Mbps
3.I go to video sources
   a. I name the video source
   b. I set the listings grabber to Schedules Direct
   c. I put in my userID and password and retrieve lineups (this works)
4.I go to input connections
   a. I give the firewire port 0 Node 1 a display ame
   b. Set its video source to the one set up in step 3
   c. Fetch channels from listing source (this works).
   d. Set the starting chnanel to a non 5c one.
5. On exiting, I run MythFillDatabase

I go to watch TV and get the error "MythTV is already using all available inputs for the channel you selected." [etc]

WTF? This is a brand new, clean install, and I haven't put in the restricted drivers, just to eliminate that problem. (So the UI is slow.) Installing the restricted drivers doesn't seem to change the above error, even though I'm now at the point where I had cross-hatcing before.

Seriously, I'm obviously missing something basic, but I can't see it. Something I've toggled to make Firewire just completely non-recognized. 

???

---

### Post by majoridiot on 2008-03-01
> **dsbw said:**
>  I haven't done tne Init Script/Primer stuff because that doesn't seem to be the problem

from what you are describing, THAT IS your problem. ... if firewire works outside of mythtv, but myth
can't use it as a tuner- AND you have not done the init script, then it is 99% likely that myth is not
treating it as a VALID tuner. because it is not primed and functional, myth THINKS that the
tuner is "busy".

this will also happen if you skip the step of giving mythtv *full* ownership of /dev/raw1394
which you might very well have skipped over, as it is included with the primers.
if you did skip it, then it's a sure killer ,too.

> **dsbw said:**
>  Believe me, if I could work this out without ever asking a question, I would... Seriously, I'm obviously missing something basic..

dude, you ARE!  please don't take my (snark-ish) RTFM comment as an insult- it wasn't meant as
such.  we are all here to help each other- which is why i wrote that guide to begin with.  PLEASE 
trust me when i assure you the BEST and SIMPLEST method of getting firewire 100% functional
with mythtv is to start at the beginning and NOT skip any steps- ESPECIALLY the ones you see no
need for.  everything in that guide is very, very important and REQUIRED for smooth operation, or it 
wouldn't be in there.

good luck! :D

---

### Post by dsbw on 2008-03-01
> **majoridiot said:**
> from what you are describing, THAT IS your problem. ... if firewire works outside of mythtv, but myth
can't use it as a tuner- AND you have not done the init script, then it is 99% likely that myth is not treating it as a VALID tuner. because it is not primed and functional, myth THINKS that the
tuner is "busy".

OK! I didn't expect that because initially the tuner was treated as available by Myth and I didn't do any of that stuff. 

> **majoridiot said:**
> this will also happen if you skip the step of giving mythtv *full* ownership of /dev/raw1394
which you might very well have skipped over, as it is included with the primers.if you did skip it, then it's a sure killer ,too.

I saw that. Again, surprised that I didn't need to do it the first time. 

> **majoridiot said:**
> dude, you ARE!  please don't take my (snark-ish) RTFM comment as an insult- it wasn't meant as such.  we are all here to help each other- which is why i wrote that guide to begin with.  PLEASE trust me when i assure you the BEST and SIMPLEST method of getting firewire 100% functional with mythtv is to start at the beginning and NOT skip any steps- ESPECIALLY the ones you see no need for.  everything in that guide is very, very important and REQUIRED for smooth operation, or it wouldn't be in there.

I understand now! I'm not thin-skinned, but I am thick-headed and I know I'm making some dumb mistakes. But some dumb mistakes are easily spotted and handled by someone with more experience, whereas a noob isn't necessarily going to see them.

For example, I was having trouble with the wget earlier. I must've typed it in a half-dozen times but I kept getting HTML instead something compilable. After leaving it alone for a few days and coming back I saw that I had put in "text" as a parm instead of "txt".

RTFM, sure. But something someone with more wget experience would've spotted instantly.  The other thing that happens (a lot) with MythTV is that you read so many different bits of help, and many of them are out-dated, so some parts apply and some don't.

Anyway, thanks for all the help. I'll go back and follow all the way through. :guitar:

---

### Post by dsbw on 2008-03-02
Well, slap my *** and call me Sally, but putting the 1394 ownership into the start/stop script did the trick.

Thanks, majoridiot! (I haven't put in the primer stuff but I will.)

Oddly, I didn't have any driver trouble this time.

Now I just have to figure out why the picture is jerky (seems to be on any live TV coming through the box, but not when I connect directly to the cable), and why changing the channel in MythTV doesn't change the STB's channel.

---

### Post by volkswagner on 2008-03-02
I believe to fix the jerky playback, you will want to change your playback settings in the frontend (utilities/setup>setup>TV settings>Playback).  For me I have deinterlace checked (linear blend), I have no custom filters, the preferred MPEG2 decoder set to  standard XvMc (libmpeg2 also worked well here), checked openGL vertical sync for timing and extra audio buffering.

Word to the wise, write down your current settings and play around see what works best for your setup.

---

### Post by majoridiot on 2008-03-02
> **dsbw said:**
> but I am thick-headed

they call me idiot for a reason, too... ;)

> **dsbw said:**
> For example, I was having trouble with the wget earlier. I must've typed it in a half-dozen times but I kept getting HTML instead something compilable. After leaving it alone for a few days and coming back I saw that I had put in "text" as a parm instead of "txt".

if you mean  the wget of the firewire_tester on that page, the link was broken for a day or so...
when i updated it *I* screwed up the link and left out the ?txt, so it was wgetting html instead
of text.  i fixed it when this was pointed out to me.  

again... we ALL make stupid mistakes ;)
> **dsbw said:**
> The other thing that happens (a lot) with MythTV is that you read so many different bits of help, and many of them are out-dated, so some parts apply and some don't.

agreed.  however, if the author and maintainer of a wiki page keeps *insisting* you need to RTFM,
then chances are you really, truly do.  

> **dsbw said:**
> Anyway, thanks for all the help. I'll go back and follow all the way through

glad it's working better for you now!  enjoy!

---

### Post by majoridiot on 2008-03-02
> **dsbw said:**
> Well, slap my *** and call me Sally, but putting the 1394 ownership into the start/stop script did the trick.

i'll leave the slapping to someone else, but happy its working for you, sally!

> **dsbw said:**
> Thanks, majoridiot! (I haven't put in the primer stuff but I will.)

you are welcome... and be sure you do- the primer is critical for reliability.

> **dsbw said:**
> Now I just have to figure out why the picture is jerky (seems to be on any live TV coming through the box, but not when I connect directly to the cable), and why changing the channel in MythTV doesn't change the STB's channel.

once you get the primer, etc. taken care of, you may need to go back into mythtv setup, delete the
firewire tuner and then re-add a new one.  i recall having to do this on occasion... it's a database quirk, i think.

---

### Post by blcvegas on 2011-03-13
I'm trying to get a firewire connection working on an SA4250.  I get a reliable connection on only a couple of channels, but it's unrelated to encryption.  I get good results with firewire tester on all unencrypted channels, yet can only get a good connection on a handful of those channels.

There seems to be no option to change the priming scripts on the more recent versions of mythtv unless I'm missing something.  Can I use a channel changing script to prime?

---

### Post by rhpot1991 on 2011-03-13
> **blcvegas said:**
> I'm trying to get a firewire connection working on an SA4250.  I get a reliable connection on only a couple of channels, but it's unrelated to encryption.  I get good results with firewire tester on all unencrypted channels, yet can only get a good connection on a handful of those channels.

There seems to be no option to change the priming scripts on the more recent versions of mythtv unless I'm missing something.  Can I use a channel changing script to prime?

You should really make a new thread and not resurrect a 3 year old one.

---

### Post by blcvegas on 2011-03-13
> **rhpot1991 said:**
> You should really make a new thread and not resurrect a 3 year old one.

Seems like a lot of times, people get asked whether they searched and read the old threads.

---

### Post by LowSky on 2011-03-15
> **blcvegas said:**
> I'm trying to get a firewire connection working on an SA4250.  I get a reliable connection on only a couple of channels, but it's unrelated to encryption.  I get good results with firewire tester on all unencrypted channels, yet can only get a good connection on a handful of those channels.

There seems to be no option to change the priming scripts on the more recent versions of mythtv unless I'm missing something.  Can I use a channel changing script to prime?

I have the same cable box and ran into a similar issue. I can change channels just fine but even on unencrypted channels it fails to lock. Sometimes it would fail a connection, so I would delete the tuner and read to have it work once again... the problem is if you tune to a encrypted channel ten try to tune to an unencrypted channel the feed will fail every time.

I decided to ease the headache and went with a Haupauge HD PVR. I still use Firewire with mythchanger to change channels as that portion works fine and never drops.

---

### Post by blcvegas on 2011-03-15
> **LowSky said:**
> I have the same cable box and ran into a similar issue. I can change channels just fine but even on unencrypted channels it fails to lock. Sometimes it would fail a connection, so I would delete the tuner and read to have it work once again... the problem is if you tune to a encrypted channel ten try to tune to an unencrypted channel the feed will fail every time.

I decided to ease the headache and went with a Haupauge HD PVR. I still use Firewire with mythchanger to change channels as that portion works fine and never drops.

Thanks for the response.  I've been keeping at this and made a little progress.  I am able to capture video on any of the non-encrypted channels using test_mpeg2.  I can only view those captured files with gnome_mplayer.  VLC and movie player both give an error of not recognizing the stream.

I read somewhere that the initial packets that the SA4250 box sends have some kind of error. If I could find some way to get a delay between channel changes and starting to capture packets, I may be able to get all channels working as expected. The priming scripts and channel changing scripts I have tried have not helped.

---

