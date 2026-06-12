---
title: "Some thoughts and/or suggestions"
date: 2007-11-24
forum: Mythbuntu
---

### Post by Just4Fun20 on 2007-11-24
As I've stated before MythBuntu is great.  It can be installed in a half hour and works pretty much as advertised.  That said, there seem to be a couple of problem areas.  For me these are: 
  1)  IR / Remote Control Operations
  2)  Video Resolution / Aspect Ratios

These lead me to consider "Troubleshooting Basics".  I've been around long enough to know that the first thing to do is search, search, search.  Sadly, this can take hours and if you don't know what you're doing can be counter productive. It's a Catch-22.  You need enough information and terminology to be able to do intelligent searches, but until you do the searches you don't understand the terminology.  Also, many problems can't easily be described in a good search argument.  

So, my first question is:  Should there be a sticky that says "start here" with suggestions on searching the forums as well as pointers to the Wiki and other sources of good diagnostic information?  

That said, to me, what is needed is specific troubleshooting sections for specific areas.  I know, I'm an engineer and think differently, but to me I'd like a guide that lists the key files, that gives an overview of the process and components and then gives troubleshooting steps.  This information can be garnered from these forums but not without a fair amount of searching and compilation of the results.  

My second questions are:  1)  In relation to my last paragraph, does such a guide exist (in my case for IR and the Remote, or for Video Resolution and Aspect Ratio).  2)  If such "troubleshooting guides" don't exist would there be value in creating them?  3)  If so, where would they be placed, in the forums or in the Wiki  (IE, in what format should they be written, clearly richer text allows better content)?  

I know, a lot of questions.  In troubleshooting my own IR/Remote problems I could create such a guide, but there's no point if it already exists or if I'm the only person that would use it.  So, this is a sort of sanity check.  

Thanks

---

### Post by superm1 on 2007-11-24
Well actually I see lots of value in such guides.  It's very very difficult for someone who works with this stuff all the time to write them unfortunately.

I think the best place to put them though would be in the installation manual.  Perhaps something in the introduction to better acquaint you with some of the basics.

We really need an improved troubleshooting section in there too.  If you would would be willing to step up to the task and help to get some of these things improved, it would be most appreciated!

I'll be glad to point you at the sources and such.

---

### Post by Just4Fun20 on 2007-11-24
That's all the encouragement I need.  I'm not promising anything but I appreciate the opportunity to contribute.  

I'll keep the mythbuntu_installation.pdf in mind for proper style and formatting, or at least for guidelines as to what is and is not allowed.  

GGK

---

### Post by superm1 on 2007-11-25
The entire PDF is written in LaTeX (and then compiled with PDFLaTeX).

To grab a copy of the sources, you will need to install bazaar.  It's in apt.

Then to grab a copy of the branch, use this command:

```
bzr branch http://bazaar.launchpad.net/~mythbuntu/mythbuntu/documentation/

```

Make any changes that you would like to the sources, and you can test by typing "make".

You will probably need some other dependencies too along the way, but you'll have to see as you go.

Once you're ready to go, you can publish your branch on launchpad.

We'll get to the details on that as you make some progress.

Thanks a lot for the help, it's most appreciated :)

---

### Post by uopjohnson on 2007-11-25
If you are writing a new guide I would be happy to help you with getting the technical details right.  I have been working with myth for a long time.  Let me know what questions come up and I would be happy to pitch in answering them.

---

### Post by superm1 on 2007-11-25
> **uopjohnson said:**
> If you are writing a new guide I would be happy to help you with getting the technical details right.  I have been working with myth for a long time.  Let me know what questions come up and I would be happy to pitch in answering them.
Well I hate to see multiple guides turn out, because the information ends up being pretty incomplete this way in one or more guides.  

This is why i'm shooting to have that installation manual have as much information as possible.  It is a great starting point for people to search for their problems, and if they don't find an answer they head to the forums, wiki's etc.

---

### Post by superm1 on 2007-11-25
Things like this are exactly what needs to be put into said guide:

[http://ubuntuforums.org/showthread.php?p=3836964#post3836964](http://ubuntuforums.org/showthread.php?p=3836964#post3836964)

I know this because i've worked with LIRC for such a long time, but clearly someone new to LIRC is a bit baffled by how a lircrc is built.

---

### Post by Just4Fun20 on 2007-12-02
I've attached a zip file (of a pdf file) that are my notes so far.  Not a 
lot and not sophisticated, but a start.  I'm currently just using a word processor and I'll convert later.  At this point I only care about content.  I'll fix structure later.  

Questions:

[LIST=1]
[*]The troubleshooting section of the installation guide does not have any complete troubleshooting guides.  Are there any good troubleshooting guides that I can use as a sample or format?  
[*]I understand the remote control up through 'lircd.conf' and running the 'irw' test.  I'm not as comfortable with things after that.  I've several questions from the '.lircrc' file forward.
[/LIST]
[LIST]
[*]A)  The 'prog' line represents the program that will receive the commands, typically "prog = mythtv".  Is there a complete list of these commands for Mythtv?  
[*]B)  In some .lircrc files there are 'prog' lines for Xine (Jaron Wilson's, which uses Xine not Mplayer).  In the default .lircrc file there are no 'prog = mplayer' lines, why?
[/LIST]
[INDENT][LIST]
[*]a)  How does Mplayer get it's commands when you're playing videos?
[*]b)  Is there a list of Mplayer commands (similar to the MythTV commands)?  Note that these are commands passed, while running, not the initial startup commands passed through the command line interface.
[/LIST][/INDENT]

My understanding of the remote control commands is that the '.lircrc' file can send them in multiple directions (I assume you could do something like 'prog= IR Blaster' to send commands that way.  Certainly you can do 'prog=xine' to send commands to xine.  

Is my understanding of the way the '.lircrc' forks commands correct?

As always, I'm just as happy with the proper terms so that I can search further.  

Thanks

---

### Post by Just4Fun20 on 2007-12-06
Superm1 (and uopjohnson) - Could one of you help me with my previous questions - I'm trying to understand the action from the .lircrc file forward.  The two big issues are: 
1)  I understand passing the commands to Mythtv but when you're playing videos you're actually using MPlayer or perhaps Xine (or even VNC).  I assume the "prog=****" line does that but wanted to verify that.    
2)  Is there a listing of the commands for Mythtv, MPlayer, Xine and VNC (and any other programs).  I've found command line commands, used when you invoke the program but not any kind of a list of keyboard commands when the program is running.  I believe these are called shortcuts but need to know how to search for them or what exactly I'm looking for.  

Thank you

---

### Post by uopjohnson on 2007-12-06
1) Yes the prog line will pass any button press to that program if it is running.  If a program is not specified in the .lircrc file it will not get button presses.  I think the use of other external players is slowly fading away as the internal player seems to be good and doesn't require nearly as much work to configure. 
As for finding the keybindings (not sure that is the official name) the best place is in mythweb (under settings, key-bindings.)  That allows you to edit the keys, but also see the current bindings.

---

### Post by Just4Fun20 on 2007-12-06
Thank you. 

This is interesting "I think the use of other external players is slowly fading away as the internal player seems to be good and doesn't require nearly as much work to configure."  

In the setup they seem to call MPlayer as the video player.  Is that what you're calling the "internal" player?  I'd gather that's true and that explains why there are no prog=mplayer lines, since the prog=mythtv is all that's needed.  

Assuming that's the case (dangerous, I know) then I also assume the that keyboard shortcuts will be the same while watching videos as while watching TV.  Is that correct?  

Thanks again.

---

### Post by uopjohnson on 2007-12-06
Nope internal and mplayer are different.  As of the last release of mythtv there is a media player built right into mythvideo called internal.  I'm not sure what it is based on.  If you go to 
Setup -> Media Setting -> Video Settings -> File Types
you will see that most of the file types are probably set to use either default or internal.  
And if you go to player settings you can change whatever is there to 'internal' to use that player as the default.

---

### Post by Just4Fun20 on 2007-12-07
> **superm1 said:**
> Things like this are exactly what needs to be put into said guide:

[http://ubuntuforums.org/showthread.php?p=3836964#post3836964](http://ubuntuforums.org/showthread.php?p=3836964#post3836964)

I know this because i've worked with LIRC for such a long time, but clearly someone new to LIRC is a bit baffled by how a lircrc is built.

```
sudo dpkg -i mythbuntu-lirc-generator_0.16-0ubuntu1+foxbuntu1_all.deb
```

What exactly does this do?  I assumed that it created (or updated) the .lircrc file after reading the lircd.conf file to know what key commands were being sent.  Why would that be preferable to simply copying in a new .lircrc file?  

TIA

---

### Post by superm1 on 2007-12-07
> **Just4Fun20 said:**
> ```
sudo dpkg -i mythbuntu-lirc-generator_0.16-0ubuntu1+foxbuntu1_all.deb
```What exactly does this do?  I assumed that it created (or updated) the .lircrc file after reading the lircd.conf file to know what key commands were being sent.  Why would that be preferable to simply copying in a new .lircrc file?  

TIA

There is a newer version available in gutsy-backports.  Fixes from that and other changes are in the version in backports.

---

### Post by Just4Fun20 on 2007-12-08
I believe it came through with the last set of scheduled updates as well.  

I'm still trying to figure out the process after lircd.conf.  What does the mythbuntu-lirc-generator do?  So far it does not seem to have affected my .iircrc file.  Should it have?  I know the .lircrc file is key to passing keyboard shortcuts to Mythtv (or a called program) so I'm at a loss to explain this new command and update.  

Any help?  

thanks

---

### Post by Just4Fun20 on 2007-12-09
superm1 and uopjohnson - Have I lost you two?  If so let me know where I've gone astray.  

So:  Remote --> lircd.conf --> .lircrc --> Program

The next step is the mappings to a program function (.lircrc --> Program).  This assumes the irw test passed correctly and that Mythtv is receiving the proper signals and translating them into the proper key (code)  sequences.  The .lircrc file maps these codes to program functions.  To determine 'program function' you need the MythTV Keyboard Shortcuts to understand what keyboard input the program will take ([http://www.mythtv.org/docs/mythtv-HOWTO-11.html]("http://www.mythtv.org/docs/mythtv-HOWTO-11.html")).    I've put them into a spreadsheet.  Note that these are from my specific installation (Hauppauge PVR-150 WinTV, which uses a PVR 350 remote.  In the Mythbuntu setup I selected "Hauppauge TV Card").  

Note that my remote does not work 'well' or as expected.  I'm not worried about it and will fix it when I've properly documented the process.  As discussed, I'll create a troubleshooting guide, which will be considered for inclusion  in the installation manual.

As a practical example, one of my problems is not being able to "escape" out of viewing a video.  With MythDora I could always push the back button to escape.  This suggests that perhaps the "Stop" button might work.  This table also explains why Ch+ and Ch- don't change the channel but instead tries to jump forward (or back).  

I still don't understand what the "update" did, or is supposed to do.  It seems I can just change, or modify, the .lircrc file to get the functions I'd like.  

Any comments?

[LIST]
[*]The first column is the "code" from the lircd.conf file.
[*]The second column "MythTV Out" is based on the .lircrc mappings.
[*]The third column is the same as the second but for Mplayer.
[*]The fourth comes from Mythtv Keyboard Shortcuts, I've aligned them to match the second column.  Where there is no match I put them at the bottom.
[/LIST]

```
Code                   MythTV Out      Mplayer Out     MythTV Keyboard Shortcuts 
---                    ----------      -----------     -------------------------
Go
Power                                  quit
TV
Videos
Music
Pictures
Guide                  S
Radio
Up                     Up              seek +60 0      Up or Down = Change Channel
Left                   Left            seek -6 0       Left = Jump set amount
Right                  Right           seek +6 0       Right = Jump set amount
Down                   Down            seek -60 0      Up or Down = Change Channel
OK                     Return          pause
Back/Exit              D                               D = Exit current recording (when watching a recording only)
Menu/i                 M                               M = brings up the program guide
Vol+                   ]               volume +1       ] or F11 = Increase Volume
Vol-                   [               volume -1       [ or F10 = Decrease Volume
Prev.Ch 
Mute                   |               mute            | or F9 = Toggle Mute
Ch+                    PgUp                            Page Up = Jump Back 
Ch-                    PgDown                          Page Down = Jump Ahead
Record                 R                               R or r = Toggle recording on or off
Stop                   Escape          quit            ESC = Quits
Rewind                 <               seek -30 0      < = (depends on mode) Backward x 10
Play                   P               pause           P = Pause/Play
Forward                >               seek +30 0      > = (depends on mode) Forward x 10
Replay/SkipBackward    Q               seek -15 0      Q or Home = Skip back to commercial break
Pause                  P               pause           P = Pause/Play
SkipForward            Z               seek +15 0      Z or End = Skip to next commercial break
1                      1
2                      2                               Type a number to enter a 
3                      3                                channel number or jump 
4                      4                                amount (HHMM format)
5                      5
6                      6
7                      7
8                      8
9                      9
Asterix
0                      0
#
Red
Green
Yellow
Blue

                                                       C = Change inputs on TV Tuner Card
                                                       I = Puts the On-screen Up
                                                       T = Toggle close caption support
                                                       F = Rotate between picture adjustments
                                                       / = Jump to the next favorite channel
                                                       ? = Mark/Unmark current channel as favorite
                                                       U = Increase play speed
                                                       J = Decrease play speed
                                                       A = Adjust time stretch
                                                       W = Cycle through zoom and aspect ration modes 
                                                       F8 = Toggle the sleep timer
                                                       CTRL-B = Jump to the beginning
                                                       + = Switch between audio streams
                                                        
```

---

### Post by superm1 on 2007-12-09
> **Just4Fun20 said:**
> superm1 and uopjohnson - Have I lost you two?  If so let me know where I've gone astray.

Haven't lost, i've just been very busy finishing my last semester here :)

> 

So:  Remote --> lircd.conf --> .lircrc --> Program

The next step is the mappings to a program function (.lircrc --> Program).  This assumes the irw test passed correctly and that Mythtv is receiving the proper signals and translating them into the proper key (code)  sequences.  The .lircrc file maps these codes to program functions.  To determine 'program function' you need the MythTV Keyboard Shortcuts to understand what keyboard input the program will take ([http://www.mythtv.org/docs/mythtv-HOWTO-11.html](http://www.mythtv.org/docs/mythtv-HOWTO-11.html)).    I've put them into a spreadsheet.  Note that these are from my specific installation (Hauppauge PVR-150 WinTV, which uses a PVR 350 remote.  In the Mythbuntu setup I selected "Hauppauge TV Card").  

Note that my remote does not work 'well' or as expected.  I'm not worried about it and will fix it when I've properly documented the process.  As discussed, I'll create a troubleshooting guide, which will be considered for inclusion  in the installation manual.

As a practical example, one of my problems is not being able to "escape" out of viewing a video.  With MythDora I could always push the back button to escape.  This suggests that perhaps the "Stop" button might work.  This table also explains why Ch+ and Ch- don't change the channel but instead tries to jump forward (or back).  

Actually, your issues of "escaping" should be resolved in the newer mythbuntu-lirc-generator available in gutsy-backports.  After it is installed, if you open up mcc and hit the checkbox to regenerate your dynamic button mappings, these buttons should work.

> 
I still don't understand what the "update" did, or is supposed to do.  It seems I can just change, or modify, the .lircrc file to get the functions I'd like.  

Yes you can, but if the automated process works, use that :)


> 
Any comments?
[LIST]
[*]The first column is the "code" from the lircd.conf file.
[*]The second column "MythTV Out" is based on the .lircrc mappings.
[*]The third column is the same as the second but for Mplayer.
[*]The fourth comes from Mythtv Keyboard Shortcuts, I've aligned them to match the second column.  Where there is no match I put them at the bottom.[/LIST]
```
Code                   MythTV Out      Mplayer Out     MythTV Keyboard Shortcuts 
---                    ----------      -----------     -------------------------
Go
Power                                  quit
TV
Videos
Music
Pictures
Guide                  S
Radio
Up                     Up              seek +60 0      Up or Down = Change Channel
Left                   Left            seek -6 0       Left = Jump set amount
Right                  Right           seek +6 0       Right = Jump set amount
Down                   Down            seek -60 0      Up or Down = Change Channel
OK                     Return          pause
Back/Exit              D                               D = Exit current recording (when watching a recording only)
Menu/i                 M                               M = brings up the program guide
Vol+                   ]               volume +1       ] or F11 = Increase Volume
Vol-                   [               volume -1       [ or F10 = Decrease Volume
Prev.Ch 
Mute                   |               mute            | or F9 = Toggle Mute
Ch+                    PgUp                            Page Up = Jump Back 
Ch-                    PgDown                          Page Down = Jump Ahead
Record                 R                               R or r = Toggle recording on or off
Stop                   Escape          quit            ESC = Quits
Rewind                 <               seek -30 0      < = (depends on mode) Backward x 10
Play                   P               pause           P = Pause/Play
Forward                >               seek +30 0      > = (depends on mode) Forward x 10
Replay/SkipBackward    Q               seek -15 0      Q or Home = Skip back to commercial break
Pause                  P               pause           P = Pause/Play
SkipForward            Z               seek +15 0      Z or End = Skip to next commercial break
1                      1
2                      2                               Type a number to enter a 
3                      3                                channel number or jump 
4                      4                                amount (HHMM format)
5                      5
6                      6
7                      7
8                      8
9                      9
Asterix
0                      0
#
Red
Green
Yellow
Blue

                                                       C = Change inputs on TV Tuner Card
                                                       I = Puts the On-screen Up
                                                       T = Toggle close caption support
                                                       F = Rotate between picture adjustments
                                                       / = Jump to the next favorite channel
                                                       ? = Mark/Unmark current channel as favorite
                                                       U = Increase play speed
                                                       J = Decrease play speed
                                                       A = Adjust time stretch
                                                       W = Cycle through zoom and aspect ration modes 
                                                       F8 = Toggle the sleep timer
                                                       CTRL-B = Jump to the beginning
                                                       + = Switch between audio streams
                                                        
```

What you are attempting to make in this table is the same problem that is attempting to be addressed with upstream lirc as well as by mythbuntu-lirc-generator, a standardization of the lirc set of buttons.  Most remotes have common buttons, and that is how mlg works.  It has a table like this stored internally with what buttons normally map well.  The problem is that it tries to work for ALL remotes, but can't because every remote has its own little idiosyncrasies.  You may consider looking at the mlg source to help build this table.  It has the mappings for elisa, mythtv, mplayer, xine, vlc, xmame all within it.

---

### Post by Just4Fun20 on 2007-12-09
> **superm1 said:**
> Haven't lost, i've just been very busy finishing my last semester here :)

Outstanding.  I wish you the very best.   

I'll keep you posted.

---

### Post by bredington on 2008-08-31
> **Just4Fun20 said:**
> As I've stated before MythBuntu is great.  It can be installed in a half hour and works pretty much as advertised.  That said, there seem to be a couple of problem areas.  For me these are: 
  1)  IR / Remote Control Operations
  2)  Video Resolution / Aspect Ratios

These lead me to consider "Troubleshooting Basics".  I've been around long enough to know that the first thing to do is search, search, search.  Sadly, this can take hours and if you don't know what you're doing can be counter productive. It's a Catch-22.  You need enough information and terminology to be able to do intelligent searches, but until you do the searches you don't understand the terminology.  Also, many problems can't easily be described in a good search argument.  

So, my first question is:  Should there be a sticky that says "start here" with suggestions on searching the forums as well as pointers to the Wiki and other sources of good diagnostic information?  

That said, to me, what is needed is specific troubleshooting sections for specific areas.  I know, I'm an engineer and think differently, but to me I'd like a guide that lists the key files, that gives an overview of the process and components and then gives troubleshooting steps.  This information can be garnered from these forums but not without a fair amount of searching and compilation of the results.  

My second questions are:  1)  In relation to my last paragraph, does such a guide exist (in my case for IR and the Remote, or for Video Resolution and Aspect Ratio).  2)  If such "troubleshooting guides" don't exist would there be value in creating them?  3)  If so, where would they be placed, in the forums or in the Wiki  (IE, in what format should they be written, clearly richer text allows better content)?  

I know, a lot of questions.  In troubleshooting my own IR/Remote problems I could create such a guide, but there's no point if it already exists or if I'm the only person that would use it.  So, this is a sort of sanity check.  

Thanks

I think it would be wonderful if someone would post the answers to how to get the Hauppauge 350 A415-HPG remote to work with ANY MythTV application.  After over 2 years of weekend research and fresh installs I finally found something while searching for the remote part number itself:

"We have only ever managed to get the Microsoft MCE Remote working completely. We use these with either the MCE Transceiver or USBUIRT Transceiver. Both of these transceivers are usb based devices. We have never managed to get any TV card direct connect transceivers working."

If ANYONE has gotten the A415-HPG remote that came with Hauppauge 150 and 350 cards to work with either IR receiver that came with same, I think there are a few people out there that would really appreciate you posting what you did.

---

