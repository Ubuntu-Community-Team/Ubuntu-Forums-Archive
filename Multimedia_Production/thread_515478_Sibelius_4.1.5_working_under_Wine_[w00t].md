---
title: "Sibelius 4.1.5 working under Wine [w00t]"
date: 2007-08-02
forum: Multimedia Production
---

### Post by stmiller on 2007-08-02
I was successful in installing Sibelius 4.1.5 under wine, and midi input and midi playback is working with the most recent wine release. Here are a few tips:

I added the wine repositories for Ubuntu from here:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

I'm using 64bit Ubuntu, though 32bit or 64bit should not make any difference.

Wine version: 0.9.42

Ubuntu Feisty 64bit with custom compiled 2.6.22.1 kernel. I recommend installing the low-latency kernel from apt-get.

After Wine is installed, make sure to run
```

winecfg

```
as your normal user (not sudo) and under the Audio tab check both the ALSA and OSS boxes.


[SIZE="4"]**Install Sibelius 4**[/SIZE]

Step 1: Install Sibelius 4 from the disc. Do not launch the autorun.exe, rather just go right to the Sibelius folder on the disc and do
```

$ wine InstallSibelius.exe

```
or whatever the exe is called.

During the install, only pick Sibelius (not the Native Instrument player or anything else) and Quicktime, unless you already have QT installed.


Step 2: I then copied all of the .dll files from a Windows XP SP2 \WINDOWS\system32 folder to my wine system32 folder located in

/home/YOU/c/windows/system32/


Step 3: Also copied the folder and all contents of \WINDOWS\WinSxS to 

/home/YOU/c/windows/WinSxS


Step 4: And lastly had to search Google for one more dll that my Windows XP install didn't seem to have:

gdiplus.dll

and place that in

/home/YOU/c/windows/system32/


Then Sibelius should start and run fine. You can start the program by doing

```

$ wine c/Program\ Files/Sibelius\ Software/Sibelius\ 4/Sibelius.exe

```
or there may be an icon installed in your Applications>Wine> menu to simply click.

I choose the register by phone option, and filled in information via an 'alternative method.'  I do own a license of Sibelius 4, though did not want to experiment with online activation.

Sibelius seemed to run sort of slow, so to speed it up, go in the prefs and make the pages and background solid colors (Ex. white paper, and grey background) rather than have it render those paper images.

[SIZE="4"][B]
Sound[/B][/SIZE]

The latest wine has lots of midi support, thanks to the wine folks. So you can configure Sibelius to work with Timidity, Qsynth, and perhaps other midi apps.

First thing is to hunt down some free soundfonts from the web. Some popular ones are

Cadenza.sf2
mustheory2.sf2
Titanic200GM-GSv1_2.sf2

and others. Then have Timidity point to a soundfont to load by editing the file /etc/timidity/timidity.cfg

comment out all the lines in the file except for one line at the bottom pointing to your soundfont on your hard drive:

```

soundfont /home/YOU/Documents/soundfonts/mustheory2.sf2

```

Then start Timidity with
```

$ sudo /etc/init.d/timidity restart

```

and when you start Sibelius, it will recognize Timidity. Alternatively, you can use **Qsynth**, load in a soundfont in its GUI, and Sibelius will recognize Qsynth (fluidsynth) as a midi sound device. I used Qsynth running with jack and had good results.
[SIZE="4"][B]
MIDI Input[/B][/SIZE]

I have an Edirol PCR-M30 USB midi keyboard, which I simply plugged in and Sibelius recognized for input with no problem. I assume any similar snd-usb-audio usb midi device will work fine also.
[SIZE="4"][B]
What doesn't work?[/B][/SIZE]

Some fonts are a little strange, mainly the time signature fonts. I think perhaps I need to copy some fonts from my Windows XP font directory, though I'm investigating. And Sibelius seems to run a little slow. It was taxing on CPU when starting or going through menu options, but when a score was loaded for input CPU usage was minimal.

This info is provided with no support and as is, etc. So if you have more success, please let us know! I haven't tried Sibelius 5 yet, but most likely it should work also. Hope this helps!

---

### Post by handy on 2007-08-03
I installed Sibelius 4.1 on Sabayon 3.4a, it went on & looks like it will work, I see the time signature font problem you mentioned in your message.

The small problem I am having is no sound comes out? ;-)

I have not copied any system files out of a windows machine, & I don't really think I will have to, I believe my lack of sound problem is somewhere between Linux, Wine & Sibelius in settings.
 
I don't require Midi recording, Sibelius is used for arranging, a small amount of composition, scanning notation, & creating tools to help teach private students, which are both recorded on CD & used directly from the notebook during lessons, printing is of course a part of the job.
  
If it would make noises I think it is almost there.

I don't need to add a SoundFont library when I have a SBLive card with it's own library on chip do I?

Your section including soundfont & Timidity is specifically preparation for your Midi use of Sibelius?

This is surely a BIG step forward, since I last tried to install Sibelius in February 2006 on Breezy.  That Wine team just keeps on keeping on... :-D

---

### Post by stmiller on 2007-08-03
Timidity comes with some free sound patches (I think?) so after installing timidity, start it as a normal user with:

```
timidity -iAq -Os
```

And then start Sibelius and see if you have sound.

When you find a good soundfont later you can then edit the /etc/timidity/timidity.cfg file to use that soundfont.

---

### Post by handy on 2007-08-03
Ok, I'll carry on with the Timidity stuff.

I actually found the Reality 32Mb SoundFont, which is a little old but still highly regarded & recommended for SBLive cards, so I'll follow your advice re' SF's too.

I just set my wife's machines up these days, I've not personally played around with music & computers since the Amiga days 1985 - 1995, so it's nice to have a guide, thanks.

---

### Post by tmth on 2007-08-10
> Sibelius 5 yet, but most likely it should work also
Sibelius 5 installer is in MSI. Is there anything i need to know before trying it?

---

### Post by sjames1010 on 2007-10-20
1. Installed timidity and wine from Synaptic.

2. Started timidity from /etc/init.d/

3. Installed Sibelius 4 using the installer,

4. Normal text fonts were all displayed as music, couldn't read anything. Copied *.ttf from my windows drive to ~/.wine/drive_c

5. registered on the phone (didn't try internet)

6. Everything worked until I got to the screen where it would try to open and display a score (even an empty one). I noticed the console output from wine mentioned an unimplemented gdiplus.dll function, so I found a copy of that dll on my windows drive and copied it into the Sibelius 4 directory.

Everything works now! Printing, displaying, editing, and sound all work.

---

### Post by Nutty Hiker on 2007-10-20
Very cool.  I'm going to have to try this with G7.  I haven't played with wine for years.

---

### Post by stmiller on 2007-10-21
Hey stjames, how are the time signature fonts looking for you? That is the only thing that doesn't display right for me. Everything else is 100% fantastic. (Including midi input with USB keyboard and midi playback with timidity.)

Just those darn time signatures! Maybe I'm missing a font? I'll try copying some fonts over, perhaps.

---

### Post by AndreGerber on 2007-10-21
Everything works wonderfully! I can even use my keyboard for output and input which I was never able to do in windows.

Thank you so much!

---

### Post by paker on 2007-11-29
> **tmth said:**
> Sibelius 5 installer is in MSI. Is there anything i need to know before trying it?
How does this change the instruction above?
Can I run xxxxxx.msi with wine just like xxxxxx.exe?
Thanks.

---

### Post by alwiap on 2007-12-11
> **paker said:**
> How does this change the instruction above?
Can I run xxxxxx.msi with wine just like xxxxxx.exe?
Thanks.

I have the same problem, I've tried to open the 'SibeliusEnglishInstaller.msi' with wine, and can't, is there a trick to do it?  Oh, and also, I'm trying to install Sibelius 5, not 4.  I would LOVE to get it to play nice with linux :)

please help!

---

### Post by christhemonkey on 2007-12-11
Try this:
```
wine msiexec /i xyz.msi
```

---

### Post by alwiap on 2007-12-11
> **christhemonkey said:**
> Try this:
```
wine msiexec /i xyz.msi
```

I did that, here is the output:
```
alex@alex-desktop:~$ wine msiexec /i SibeliusEnglishInstaller.msi
err:msi:copy_package_to_temp failed to copy package L"SibeliusEnglishInstaller.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002!

```

Additionally, a prompt came up that said 'The specified installation package could not be opened. Please check the file path and try again.'

Is there another file, then, that will autorun the program?  There is an autorun.inf file in the main directory, but I have NO idea how to open that.  I'll keep fooling around.

EDIT: I changed the directory to where the file was (cd /media/cdrom0/Windows/Sibelius) and it worked fine!  Doh, I'm stupid!  I'll report back with if I got it working or not, I'd like to make a noobie HowTo because I'm sure I'm not the only one that wants to get Sibelius 5 working in linux as easily as possible!  I could ditch my dual-boot with XP then :)

---

### Post by alwiap on 2007-12-11
I installed Sibelius 5 successfully (I think) and when I try to open the program on my desktop, it says 'The Microsoft .NET Framework is not installed, you can install it on the CD'.

So I explored the files on the DVD, I found in the 'Windows' folder a .exe called 'dotnetfx.exe'.  I opened that file, and it said 'Setup has detected that the following prerequisite programs are not installed: Microsoft Internet Explorer 5.01'

So I went to [http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation) and installed IEs4Linux, I believe I installed Internet Explorer 6.0 (would I NEED to install 5.01?  I don't think it was an option there), and I re-ran the 'dotnetfx.exe' file, but it still says the same thing.

Any ideas?

EDIT:  I also tried Internet Explorer 5.0 and 5.5, no luck.

---

### Post by alwiap on 2007-12-12
bump!  i really need to use this in linux :)

---

### Post by stmiller on 2007-12-12
Sibelius 5 may be a different animal, as it includes lots of Native-Instruments playback stuff which is not so wine friendly. 

Is there a way in the Sibelius 5 install to only install the bare Sibelius program and NO kontakt player stuff? That is my only suggestion. I don't have a copy to try out. (Only Sib. 4).

---

### Post by alwiap on 2007-12-12
> **stmiller said:**
> Sibelius 5 may be a different animal, as it includes lots of Native-Instruments playback stuff which is not so wine friendly. 

Is there a way in the Sibelius 5 install to only install the bare Sibelius program and NO kontakt player stuff? That is my only suggestion. I don't have a copy to try out. (Only Sib. 4).

I don't think so, no.  It asks that the .NET framework has to be installed and I can't seem to install that correctly, that is my only stumbling point so far, I'm googling to find an answer for that.  The installer won't let me proceed past the .NET framework point, and the .NET framework installer on the Sibelius DVD requires me to have IE 5.01 or higher, which I have installed, but it still doesn't work.  :confused:

---

### Post by djbon2112 on 2008-01-27
Here's the Musica Theoria 2 soundfile, took me forever to find and since it's so highly recommended, I think it needs a place here.

[http://rapidshare.com/files/87129093/mustheory2.sf2.html](http://rapidshare.com/files/87129093/mustheory2.sf2.html)

---

### Post by stmiller on 2008-03-07
After having trouble with a few later wine releases, Sibelius 4 is working fine for me with wine 0.9.57.

Time signature and key signatures still don't display quite right. But timidity playback works great.

---

### Post by Ryuki_NdranC on 2008-04-22
Im i have sibelius 5 put so far i have readed, isn't working under wine. I did a virtualbox but im afraid of ruining it there with one 1 gb of ram in my laptop :(

Maybe i should consider get sibelius 4. If anyone has any output about sibelius 5 i'll be apreciated.

Thx for the tutorial, a real treat :)

---

### Post by bluemorris on 2008-05-25
This is working for me too, with Sibelius 4! Thanks!

But... one other problem I have found is that I can't select any text on the page to move it around like you can in Sibelius in Windows (i.e. just click on the text and drag it anywyere, or click on it to edit the text).

Anyone else have this problem? I'm wondering if it's just me.

Thanks,
Blue

---

