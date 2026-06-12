---
title: "Too quiet microphone in skype"
date: 2006-03-12
forum: Multimedia &amp; Video
---

### Post by Rzulf on 2006-03-12
Why in skype the microphone is so quiet. When I use M$ the microphone is much more lauder. I set the highest possible volume for microphone.

---

### Post by aysiu on 2006-03-13
I don't know if you're in Gnome or KDE, but in KDE, KMix allows you to activate "mic boost."

---

### Post by Rzulf on 2006-03-13
It increases volume of microphone on my computer but not when I talk to somebody on skype. Btw. I use Kubuntu :)

---

### Post by sirlancelot on 2006-07-31
I am having this same exact problem, I can hear myself fine when I test the mic in KDE, but when I talk to someone on Skype, they have to turn their speakers up to the max and can still barely hear me :(

Anyone know why? I've done the mic boost and it still doesn't fix it...

---

### Post by pollock.tar.gz on 2006-08-23
same exact problem here

---

### Post by mobilehavoc on 2006-08-30
> **pollock.tar.gz said:**
> same exact problem here
Same problem here, I have microphone boost enabled and mic volume set at max. It's incredibly quiet.

---

### Post by balmar on 2007-01-02
I had the same problem: incredibly quiet microphone in Skype 1.3.0.53_API even after trying all volume controls and micro boost in alsamixer. What seemed to help was copying this stuff:
[http://forum.skype.com/lofiversion/index.php/t45129.html]("http://forum.skype.com/lofiversion/index.php/t45129.html")
for my Ubuntu Edgy Eft. That is:
--> exit Skype
--> find the file ~/.Skype/shared.xml
--> below the line "<VoiceEng>", insert "<AGC>0</AGC>"
--> two lines below I had "<MicVolume>21</MicVolume>", and changed it to     "<MicVolume>250</MicVolume>".
--> find the file ~/.Skype/[your Skype username here]/config.xml
--> below the line "<Call>", insert again "<AGC>0</AGC>"
--> start Skype and test your micro with echo123. Now it worked for me (with micro level on max and micro boost +20db in alsamixer).

Hope it works for you guys as well.

---

### Post by IamAcoconut on 2007-01-11
Goddamn!

I did what you said, **balmar**, and also followed the instructions here [http://ubuntuforums.org/showthread.php?t=312237](http://ubuntuforums.org/showthread.php?t=312237)
but still - it is extremely quiet! Do I really have to switch systems to make my microphones work?
Please help :(

---

### Post by balmar on 2007-01-11
> **IamAcoconut said:**
> Goddamn!

I did what you said, **balmar**, and also followed the instructions here [http://ubuntuforums.org/showthread.php?t=312237](http://ubuntuforums.org/showthread.php?t=312237)
but still - it is extremely quiet! Do I really have to switch systems to make my microphones work?
Please help :(

I'm really not an expert to be able to help you... :( I would try to check if the mic works ok outside skype, and if yes, then google further along the lines AGC, MicVolume, etc...

---

### Post by IamAcoconut on 2007-01-13
It's not only a Skype issue. It's very quiet in all apps.

---

### Post by balmar on 2007-01-14
> **IamAcoconut said:**
> It's not only a Skype issue. It's very quiet in all apps.

Have you tried with another mic? Or have you tried the same steel with Windows?

---

### Post by IamAcoconut on 2007-01-14
I tried two different mics. In Windows they're working OK :<

---

### Post by balmar on 2007-01-14
> **IamAcoconut said:**
> I tried two different mics. In Windows they're working OK :<

Well, my last idea would be to open Volume Control (right-click on the speaker icon on the panel, or you might have to add it to your panel if it's not there), Then click the 
Playback tab,
go to
Edit --> Preferences,
select everything you see there. Then proceed with the
Capture tab,
and again
Edit --> Preferences,
select everything. Then do the same with the Switches and the Options tabs. So now you have all possible controls and switches. (At least this is how it looks in Edgy Eft.) Play with them and see if your mic gets better. I think it's basically the same as opening alsamixer and setting all kind of stuff there.

---

### Post by likwid on 2007-01-14
I'm having the exact same problem in gnome. It's really a hindrance as i'm trying to get my girlfriend out of the habit of booting Windows and if she can't use skype then i've got no chance..

Anyone find a solution??

---

### Post by IamAcoconut on 2007-01-15
My <MicVolume> value was 256 by default, which appears to be the highest (I tried to set it to 700, but it kept reverting to 256), so the problem is with Ubuntu, not Skype.
There are so many threads about it, and still no solution :|

---

### Post by dvarsam on 2007-01-26
[QUOTE=aysiu]I don't know if you're in Gnome or KDE, but in KDE, KMix allows you to activate "mic boost."[/QUOTE]

I am having the same problem too!
The microphone is very silent.
I am using Ubuntu v6.10 (Edgy - Gnome) with all updates installed!

Inside "skype" there is a "test" your Hardware option...
When I installed "skype", an automated recorded message played (i.e. a lady) asking me to test my hardware (speakers & microphone).
I could listen to her voice crisp & clear!
Then she asked me to record a 10 seconds message by speaking on the mic...
I did this, but when it was time to hear my recorded message, I could barely listen to myself...
Even if you boost your speakers to max, you barely hear yourself...!!!

Thanks.

P.S.> I am NOT connecting to a "budda" far-away land, nor to the US Space Station... this is all performed locally... My Goodness, this sucks!!!

---

### Post by crane on 2007-01-26
I'm having issues as well. It's not just Skype but audacity as well. When I do get the volume up where I can hear my voice there is a squelling sound. This seems to be an OS problem and not a specific app.

---

### Post by dvarsam on 2007-01-27
[QUOTE=crane]I'm having issues as well. It's not just Skype but audacity as well. When I do get the volume up where I can hear my voice there is a squelling sound. This seems to be an OS problem and not a specific app.[/QUOTE]

From my experience, after the installation of "skype" all hell breaks loose...
For example, if from the Menu, I select "Applications\Sound & Video\Sound Recorder", when I try to playback my sound recorded, I need to put the speaker's volume in max & still I hear my sound recording with difficulty...

I guess that the installation of "skype" affects other important parts/programs of Ubuntu...
That is only an "opinion" of course, and you would have to perform some tests in order to prove this...

Thanks.

---

### Post by crane on 2007-01-27
The only thing that keeps me from blaming skye is that am am running skype from a directory. I did not "install" skype. It can be downloaded unzipped and ran. So I do not see it effecting the system at all. I am now running Dapper again.
 I have searched, tweaked, and configed until I am tired of messing with it. maybe edgy is still to edgy. Who knows. Dapper is where I will have to remain.

---

### Post by IamAcoconut on 2007-01-28
> **crane said:**
>  I am now running Dapper again.
 I have searched, tweaked, and configed until I am tired of messing with it. maybe edgy is still to edgy. Who knows. Dapper is where I will have to remain.
Do you mean it''s OK in Dapper? 
I was using Dapper when I first posted in this thread.
Now I have Edgy, and it's still ****** up. I'm afraid VMware is the only 'solution'.

---

### Post by crane on 2007-01-28
Yea, Dapper works great for me so I am back to it. I hope this gets resolved soon.

---

### Post by dvarsam on 2007-01-29
[QUOTE=crane]The only thing that keeps me from blaming skye is that am am running skype from a directory. I did not "install" skype. It can be downloaded unzipped and ran. So I do not see it effecting the system at all. I am now running Dapper again.
 I have searched, tweaked, and configed until I am tired of messing with it. maybe edgy is still to edgy. Who knows. Dapper is where I will have to remain.[/QUOTE]

You downloaded, unzipped & run it (without installing), how?

By using the program "klik" - i.e.:

[http://klik.atekon.de/](http://klik.atekon.de/)

Note: Many thanks to user "RAV TUX" for providing this...

Thanks.

P.S.> This is a smart workaround you thought of...
Very good one!!!

---

### Post by crane on 2007-01-29
On [skype's site]("http://www.skype.com/download/skype/linux/") there are different packages to install. The "[Static binary tar.bz2 with Qt compiled in]("http://www.skype.com/go/getskype-linux-static")" package can be extracted and ran from it's directory.
 This was a few versions ago so I'm not sure if it is the same now. Doing this shouldn't change any sound settings on the system.

---

### Post by dvarsam on 2007-01-29
Thanks man, you are great!!!
This is even better!
It just runs by itself!
(i.e. it does not require the installation of "klik" or some other program...)

_Extended Version - Improvement_:
It would also be cool, if you could have this package/program lying in a USB Stick & just be able to plug it in _any_ PC OS (i.e. Windows & Mac too! - not just Linux) and run the app without needing to install it!!!
That would be super!!!
No matter whether you have a PC or NOT (i.e. you are on the way & don't own a Laptop), with a simple USB Stick, you enter an Internet Cafe (or hijack your friend's PC) & Voice Chat right away!!!
Imagine also Street Payphones with a USB jack, where you plug your USB Stick & instead make your Phone Call through your Skype account...
Your bill is charged on your Skype account & you neither need coins nor calling cards any more...
Awesome!!!

Thanks.

---

### Post by dvarsam on 2007-01-29
[QUOTE=crane]On [skype's site]("http://www.skype.com/download/skype/linux/") there are different packages to install. The "[Static binary tar.bz2 with Qt compiled in]("http://www.skype.com/go/getskype-linux-static")" package can be extracted and ran from it's directory.
 This was a few versions ago so I'm not sure if it is the same now. Doing this shouldn't change any sound settings on the system.[/QUOTE]

I just tested it, man!!!
IT WORKS!!!
IT WORKS!!!
Someone throw some fireworks in the Forums!!!
Someone please create a "Smilie" with Fireworks!!!

It was awfully simple!!!

**_Step-by-Step HowTo Install/Use_:**

1. Download the "[Static binary tar.bz2 with Qt compiled in]("http://www.skype.com/go/getskype-linux-static")".
2. Double-click the downoaded package lying on your desktop.
3. On the new window that opens up, select the Folder shown inside (it is only 1 - hard to miss it :)!).
4. Click on the button named "extract" & extract the program's Folder on your Desktop.
5. Double-click on the extracted Folder lying on your Desktop.
6. Double-click on the Skype's Icon to run it (i.e. the big "S" icon).
7. Perform a "test" your speaker & mic - it will turn out to be successful...
8. Have fun using the Program!!!

This is awesome!
Many thanks!

---

### Post by crane on 2007-01-29
> **dvarsam said:**
> I just tested it, man!!!
IT WORKS!!!
IT WORKS!!!
Someone throw some fireworks in the Forums!!!
Someone please create a "Smilie" with Fireworks!!!

It was awfully simple!!!

**_Step-by-Step HowTo Install/Use_:**

1. Download the "[Static binary tar.bz2 with Qt compiled in]("http://www.skype.com/go/getskype-linux-static")".
2. Double-click the downoaded package lying on your desktop.
3. On the new window that opens up, select the Folder shown inside (it is only 1 - hard to miss it :)!).
4. Click on the button named "extract" & extract the program's Folder on your Desktop.
5. Double-click on the extracted Folder lying on your Desktop.
6. Double-click on the Skype's Icon to run it (i.e. the big "S" icon).
7. Perform a "test" your speaker & mic - it will turn out to be successful...
8. Have fun using the Program!!!

This is awesome!
Many thanks!

Once you are sure everything is working. You can move the folder out of home directory.
I put mine in the /opt folder. Then just create a shortcut or add a an icon to your task bar and make sure the path is pointing to where ever you put the folder. This will help keep your home directory from cluttering up. 
When an updated version is released just install it the same way and edit the executables.
All your settings are actually stored in a hidden folder in your home directory. I beleive it is name .skype.

---

### Post by Titi on 2007-01-30
so does this actually solve the quiet mic thing? 'cause i have skype installed (the normal way) and my microphone is very silent, but i don't know how it was before :)
so by removing skype and installing it this way, my mic should sound louder?

---

### Post by crane on 2007-01-30
> **Titi said:**
> so does this actually solve the quiet mic thing? 'cause i have skype installed (the normal way) and my microphone is very silent, but i don't know how it was before :)
so by removing skype and installing it this way, my mic should sound louder?

Not sure about that. You can download the version we mentioned and run it without uninstalling the other. You may want to rename or move your .skype file to be sure no current settings will effect it.

---

### Post by dvarsam on 2007-01-30
[QUOTE=Titi]So does this actually solve the quiet mic thing? 'cause i have skype installed (the normal way) and my microphone is very silent, but i don't know how it was before :)
so by removing skype and installing it this way, my mic should sound louder?[/QUOTE]

Hello!
I did this & it worked successfully without the need to uninstall "skype".
I then decided to get rid of the installed program "skype' & start using the non-installable version instead.
So, I opened up Synaptic & removed "skype".
Now it seems that my microphone is NOT working again!... lol
(And that happens when from the Menu I select "Applications\Sound & Video\Sound Recorder".
I record sound but I can't hear a thing...!!!)
I then tried to test the non-installable version of "skype" but it would not work either...!

So, I don't know what to tell you...
Can you tell us your experience?

Thanks

P.S.> I think I should format the Hard Drive & re-install...
I don't see this getting fixed in any other way...

---

### Post by crane on 2007-01-30
> **dvarsam said:**
> Hello!
I did this & it worked successfully without the need to uninstall "skype".
I then decided to get rid of the installed program "skype' & start using the non-installable version instead.
So, I opened up Synaptic & removed "skype".
Now it seems that my microphone is NOT working again!... lol
(And that happens when from the Menu I select "Applications\Sound & Video\Sound Recorder".
I record sound but I can't hear a thing...!!!)
I then tried to test the non-installable version of "skype" but it would not work either...!

So, I don't know what to tell you...
Can you tell us your experience?

Thanks

P.S.> I think I should format the Hard Drive & re-install...
I don't see this getting fixed in any other way...

 I'm not sure if a reinstall would fix it. Have you done something that would mess it up?
I think it may be sound a deeper issue than skype. I cannot get mine working either. I am currently using my head set from the PS2 game Socam to talk in Skype. But this still does not change audacity. I cannot change what device to use in it's settings. 
Sound has always been an issue with linux in general.

---

### Post by petermck on 2007-02-09
I recently installed skype and had similar problems to what I've seen described here; mic too quiet and recording in sound recorder not working. I found the fix for both problems to make sure the correct capture device is selected in System->Preferences->Sound and check Mic Boost in the volume control panel preferences.

---

### Post by crane on 2007-02-09
I have tried this with no success. I was able to get a socom headset to work but still no luck on mic inputs.

---

### Post by dvarsam on 2007-02-09
[QUOTE=crane]I have tried this with no success. I was able to get a socom headset to work but still no luck on mic inputs.[/QUOTE]

Well, in my opinion:
Don't believe everything you read...
Whenever I ask something, everybody says "it exists"!!!
But when I need more info...
... forget it man...!!!
Thanks.

P.S.> You better wait for Feisty Fawn instead...):P

---

### Post by ushaba on 2007-03-01
i don't think this is a skype specific problem. i am currently running kubuntu 6.10 and have had exactly the same problems you have all described with audio before installing skype. i just installed skype, of course, as it's a convenient test of whether or not things are working, but i was not getting sound in audacity or sound recorder or anything else either. 
no idea waht the problem is. it picks up clicks on the microphone (for on/off) but nothing else. i have two sound devices on this motherboard, so i am wondering if that is a common situation for others.  but yes, i was having this problem before skype on this install.

---

### Post by dannyboy1121 on 2007-03-10
Running Edgy + an Audigy sound card - Hmmm ... I have the volume settings open and skype open. I set the microphone capture level to maximum - run the skype test and the capture volume drops in front of my eyes. I drag it back up - a second later it drops back down. :confused:

---

### Post by bluenova on 2007-03-10
> **dannyboy1121 said:**
> Running Edgy + an Audigy sound card - Hmmm ... I have the volume settings open and skype open. I set the microphone capture level to maximum - run the skype test and the capture volume drops in front of my eyes. I drag it back up - a second later it drops back down. :confused:

The reason for this is Skype auto adjusts your volume to get it at a nice level. The reason yours keeps going way down is probably because you have a mix being captured causing a feedback loop. What you need to do is go to the volume control and set:

On playback: Mic off, Analogue mix off (speaker with red X through it.)

On Capture tab: Goto edit prefs, and make sure everything is ticked. Give red X's for everything (speaker and mic icons) apart from the Mic, and put the volume on full (Skype might adjust it a bit afterwards)

---

### Post by likwid on 2007-03-11
In volume control click in preferences and enable microphone capture. Check that the microphone icon isn't crossed out, as it was in my case.

---

### Post by atmartin50 on 2007-04-23
Hi Crane and dvarsam,

Thanks a bunch for your instructions on how to install Skype. After tons of problems installing and using Skype after upgrading from Edgy to Feisty, I'm finally up and running.

However, I'm not able to move that extracted folder from my desktop to the /opt folder---it's saying that I don't have permission to move the folder. How can I remedy this? Forgive the question; I'm an Ubuntu newbie.

Also, Skype is not present in Applications-Internet. How can I set it up so that it is? I'd really like to have an icon on my panel.

One more question....should I delete the .Skype folder from my home folder now (it's from a previous version)? Will it affect my current setup if I do?

Thanks a bunch for your help!!! This forum is great, as are its users!

---

### Post by Neecapp on 2007-04-23
To get your mic to work.. you should check out alsamixer.

(press tab)

it will bring up your input options 

Make sure ADCMux is on... it should say something along the lines of
L   R
CAPTUR

Then make INMUX 100.
Then make INVOL 100.

Tab again.

Go all the way to the right.. and make sure the right Input Source is selected (Mine is Front Mi) For Front Microphone inlet.

After that everything worked great in Skype.

Call up the tester and test it out.


Good luck,
Neecapp

---

### Post by crane on 2007-04-23
> **atmartin50 said:**
> Hi Crane and dvarsam,

Thanks a bunch for your instructions on how to install Skype. After tons of problems installing and using Skype after upgrading from Edgy to Feisty, I'm finally up and running.

However, I'm not able to move that extracted folder from my desktop to the /opt folder---it's saying that I don't have permission to move the folder. How can I remedy this? Forgive the question; I'm an Ubuntu newbie.

Also, Skype is not present in Applications-Internet. How can I set it up so that it is? I'd really like to have an icon on my panel.

One more question....should I delete the .Skype folder from my home folder now (it's from a previous version)? Will it affect my current setup if I do?

Thanks a bunch for your help!!! This forum is great, as are its users!
If you are unfamiliar with the console. Th just type ```
gksu nautilus
```
in a terminal. It will then ask for a pass ward and open a nautilus terminal as root user.
Then just navigate to the skype folder you want in opt. Right click and select cut. Then navigate to the /opt folder and select paste.
If you are familiar with console just use sudo command to move the folder to opt.
[CODE]sudo mv -R /home/youHome/Desktop/Name_of_files /opt/name_of_file/CODE]
As far as adding to the menu, i am not too sure. I've never added anything to the menus. To add it to the task bar, just right click on the task bar and select add to  panel> custom application launcher. The enter the info as needed and click OK.
You should be able to just delete the older folder with no problems. Just send it to your trash for a few days and make sure the new version is working OK. Then just empy your trash.

---

### Post by jackmc on 2007-04-24
> **likwid said:**
> In volume control click in preferences and enable microphone capture. Check that the microphone icon isn't crossed out, as it was in my case.

Thanks, that did it for me :)

---

### Post by atmartin50 on 2007-04-24
Thanks crane,

That worked like a charm! I appreciate your help! I'm finally up and running again. It's curious that my mic seems much more sensitive now (maybe that's just a default setting for Feisty which I can tweak) than it was in Edgy. But the reception seems great overall.

The only other curious thing that happened while installing this version of Skype is that the tone before my voice mail is now extremely loud and cacophonous, according to a friend that called me. I wonder how that could be?

---

### Post by crane on 2007-04-24
Not sure about that, could be a setting in Skype. Be sure to check any read mes or skyes faq pages. There may be some help there as well.

---

### Post by samuliri on 2007-04-28
I had same problem. This is what I did, and it worked:

1) Double click Volume control in the panel  => Volume control window opens.
2) Edit / Preferences: check all  =>  four tabs appear
3) Recording tab:  capture 100%
4) Switches tab, check: mic capt. & mic boost & IEC958
5) Options tab: Shared/Mic1/AC-link/Mix/2ch/AC-link
6) Playback tab: Master 100%  & PCM 100% & Line-in 100% & CD 70% & IEC958 0% & PC Speakers 100% - all other off

---

### Post by Dave Otter on 2007-04-28
This solved it for me 
             Vol.Control--Switches-enable Mic Boost
                                     Dave

---

### Post by cpudney on 2007-06-27
G'day,

I had this problem ([quiet microphone capture in Skype and Sound Recorder on Dapper with a Dell Inspiron 9400]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2007/06/microphone-audio-capture-very-faint.html"), i.e. external microphone, no builtin mic).

The solution was that provided above by Neecapp, use alsamixer to bring up the levels for Capture and make sure ALSA is used in Skype.

Cheers,
Chris.

> **Neecapp said:**
> To get your mic to work.. you should check out alsamixer.

(press tab)

it will bring up your input options 

Make sure ADCMux is on... it should say something along the lines of
L   R
CAPTUR

Then make INMUX 100.
Then make INVOL 100.

Tab again.

Go all the way to the right.. and make sure the right Input Source is selected (Mine is Front Mi) For Front Microphone inlet.

After that everything worked great in Skype.

Call up the tester and test it out.


Good luck,
Neecapp

---

### Post by jeremysan on 2007-07-20
> **balmar said:**
> Well, my last idea would be to open Volume Control (right-click on the speaker icon on the panel, or you might have to add it to your panel if it's not there), Then click the 
Playback tab,
go to
Edit --> Preferences,
select everything you see there. Then proceed with the
Capture tab,
and again
Edit --> Preferences,
select everything. Then do the same with the Switches and the Options tabs. So now you have all possible controls and switches. (At least this is how it looks in Edgy Eft.) Play with them and see if your mic gets better. I think it's basically the same as opening alsamixer and setting all kind of stuff there.

balmar, I tried your instructions and people were able to hear me on Skype :D.

---

### Post by Sparky222B on 2007-08-01
This fixed it for me:
[http://ubuntuforums.org/showthread.php?p=3118306](http://ubuntuforums.org/showthread.php?p=3118306)

---

### Post by anemptygun on 2008-02-24
> **balmar said:**
> Well, my last idea would be to open Volume Control (right-click on the speaker icon on the panel, or you might have to add it to your panel if it's not there), Then click the 
Playback tab,
go to
Edit --> Preferences,
select everything you see there. Then proceed with the
Capture tab,
and again
Edit --> Preferences,
select everything. Then do the same with the Switches and the Options tabs. So now you have all possible controls and switches. (At least this is how it looks in Edgy Eft.) Play with them and see if your mic gets better. I think it's basically the same as opening alsamixer and setting all kind of stuff there.

Hurray that worked! thank you balmar!

---

