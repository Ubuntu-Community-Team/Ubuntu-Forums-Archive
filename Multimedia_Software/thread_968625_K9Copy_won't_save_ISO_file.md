---
title: "K9Copy won't save ISO file"
date: 2008-11-02
forum: Multimedia Software
---

### Post by Luft on 2008-11-02
I'm using K9Copy to convert my DVD's into ISO files that I save on my server and use VLC to play them.  The problem is that since I upgraded to Ubuntu/Kubuntu 8.10 K9Copy no longer saves the files it creates.

It acts like it is creating the file.  I see the previews as it works its way through the DVD but after it finishes I look in the location I told it to store the ISO file and it isn't there.  I have searched to see if it is storing it somewhere else but it simply isn't saving it.

---

### Post by kngunn on 2008-11-03
Same here with Ibex, buy I'm trying to create an mpeg-4.  Everything completes successfully, but no file -- even did a find from the command line with no luck.

---

### Post by larryn28 on 2008-11-03
same problem here, tried it several different times & it never produces the iso file, prior to 8.10 it would automatically open k3b and allow it to be burned immediately. now all it does is produce audio & video_ts folders. any help would be greatly appreciated.

---

### Post by mc4man on 2008-11-03
Tried k9 in the kde4 ver.(8.10) and it worked fine (i saved the iso to the desktop or what is called the desktop. (can't quite figure that out yet

---

### Post by RussW210 on 2008-11-05
I was having the same problem as the guy above.  It would only create two folders, and separate the movie into .VOB files.  Wouldn't create the .iso.

However, tried burning the iso to the "Desktop" folder and it ripped it right as an .iso.  Bug that needs to be worked out, but it worked fine none the less from there.

At least my DVD Authoring works in k9copy now since upgrading from 8.04 to 8.10.  Not that I'm going to use it.

---

### Post by RussW210 on 2008-11-05
Nevermind.  I selected part of the dvd and it ripped it as an iso.  But when I copied the actual DVD it still created the two folders (AUDIO and VIDEO).  k9copy is useless to me unless it can create the single .iso file.  If anyone has any idea how to fix/get around this, please let me know.

---

### Post by RussW210 on 2008-11-05
I think the problem actually stems from the format of my hard drive.  I rip certain pieces of the movie without a problem.  It will create a dvd folder, a few temporary files, but the .iso file also gets created.  Then I just delete the rest.

However, when I try to rip the whole dvd, no .iso file gets created at the end.  Just everything else.

Is this a FAT32 vs NTSC issue?  I overheard something about not being able to save a file on a FAT32 hard drive that is over 4gb.  The full movie would come in over that.

I have a Dell Inspiron 530 and am saving to my internal hard drive.  I never formatted the hard drive.  Is there a way to tell if it is FAT32?  Would that be the problem?

This whole thing started when I upgraded from 8.04 to 8.10 ubuntu.  It used to create a single .iso file, now it doesn't.  Not sure why it created an .iso file in 8.04 but not anymore in 8.10.

PLEASE HELP!!!

---

### Post by becatlibra on 2008-11-07
same problem here - 2 folders and a tmp file - no ISO

---

### Post by rfurman24 on 2008-11-16
Mine worked after a little playing around. I have to do everything I normally do then select copy with the output still selected to iso. Hope this helps.

---

### Post by Kevrox on 2008-11-22
having same issue after hardy to intrepid upgrade Gnome ... cannot find a solution yet... launchpad.net has not given any answers yet either...

rfurman24: what "playing around " worked for you? perhaps share some of  your setting please.
Thanks
Kev

---

### Post by jondecker76 on 2008-12-02
i'm having the exact same problem here using 0810. The autio_ts and video_ts folders get created, but no .iso file is created. It has always worked for me in the past, until I upgraded to -0810

---

### Post by kuroyagi on 2008-12-03
Me too. Here is the same problem. Do you use a amd64 box? I gues the problem happened in a amd64 box, don't you?

Now I'm using the k9copy package of Hardy. It works fine...

---

### Post by Kevrox on 2008-12-04
I found the solution to my k9copy no iso problem Finally.

I have 2 dvd burners and old i/o connected pioneer 109 and a newer sh-s203d sata connected...
The Sata connected one was the issue after many many tries I finally used my old dvd burner and .... my old i/o connected pioneer worked like a charm...
so I think there might be an issue with intrepid sata drivers...  hope this helps someone.

---

### Post by Kevrox on 2008-12-04
seems sata drivers are sorted... I took the risk of updating the 27.9 kernel to 27.10.. by allowing the pre-release updates and did the burns and rips again and this time iso files were created... worth a try but at own risk as the updates could stuff something else up...

---

### Post by Kevrox on 2008-12-19
I have the sata dvd burner drive working in Hardy and k9copy... not sure what did it but 2 things I have done this week.
1. I flashed my motherboard with the newest flashy stuff from the manufacturer. So that is now up to date, seems the hard drive is not so fussy now too.
2. Nice clean install of hardy with a super 1 sudo install command from terminal that I made up.. This like codecs and other programs i use all the time. So instead to taking me a day or two it happens all at once... love terminal commands once you know what you are doing.

So Flash motherboard if you can ( at own risk) and that might do it...

A little later that day

Ok I can confirm that this was MY solution... hope it helps others...
I can now back up our dvd's and have spaces in the title save as.... yes SPACES..... SO do not rely on computer stores to supply you a new machine with up to date flashed Motherboards, even burning the iso had NO issues... Happy Christmas everyone!!!

---

### Post by dstock76 on 2008-12-28
I'm having the same problem.  It will create the iso file on the desktop but not on my ntfs drive or ext3 drive.  Strange, I don't get it?

---

### Post by MightyFlea on 2009-02-12
It seems I have the same problem: k9copy would read the DVD and create files in the Video_TS directory, but no ISO file (and trying to burn directly with k3b also failed).

Here is what worked for me in the end:
After k9copy had finished and failed to create the ISO, I opened k3b, created a new Video DVD project and added the Audio_TS and Video_TS directories to it, then burned the project.
The resulting DVD did play both in my computer and on my DVD player.

Hope this helps.

---

### Post by EvilGnome on 2009-02-15
Having the same problem here on Intrepid 64, very frustrating

---

### Post by smuggly on 2009-06-03
Install libdvdcss2 And It Solves The Problem! Through Synaptic Or Apt Either One.................Smuggly
libdvdcss2 isnt in restricted any more.

---

### Post by smuggly on 2009-07-08
Well im back to the same no iso problem again.After reboot i think.I Gave dvd 9 to 5 a try and it works great.Im using gnome though.Until k9copy fixes it give it a try......smuggly

---

### Post by r_avital on 2009-10-07
Hello all, and very sorry to bother you with this again, but I have the same problem even after trying/checking what was posted above.

* Ubuntu Jaunty, 2.6.28-15-generic.  Plays DVDs with no issues, from any region.
* k9copy v2.3.0 using KDE 4.2.2 (running under gnome, but KDE4 is fully installed)
* Gave path in the "save" dialog as: /home/myhomedir/dvdtemp/abcdefg.iso - No spaces, no underscores.
* Tried the above with and without the ".iso" extension.
* My DVD drive is IDE. The only SATA device on this system is the hard drive (ext3 formatted).

k9copy goes through the motions, shows me the preview screen, creates the AUDIO_TS and VIDEO_TS directories where I specified in the configuration panel, and the rest of the files under VIDEO_TS as well.  No ISO file anywhere to be found.

Any assistance would be greatly appreciated. Many thanks in advance to all.

---

### Post by newyorkpaulie on 2009-12-11
> **rfurman24 said:**
> Mine worked after a little playing around. I have to do everything I normally do then select copy with the output still selected to iso. Hope this helps.Can you please explain what you meant by "playing around"? I get the 2 folders (audio & video), but no .iso file. Tried saving to desktop as someone said worked for him but no dice. I can make the copy by rightclicking on the video file once k9 has gotten that far but I want to save each one as an .iso for reburning later.

---

### Post by newyorkpaulie on 2009-12-12
I got mine to work, finally. I created a folder on my external drive (on my docking station) called DVDs. The trick here is that you need a large enough place to store the .iso otherwise the program will not create the file or even let you know the reason it doesn't (lack of room). Then I opened k9copy - went to Settings/Configure k9copy - on the left panel I chose DVD - and then entered the path to the place I wanted to put the iso file, namely on the (roomy enough) external hard drive. It works!

---

### Post by r_avital on 2009-12-13
Thanks Paulie, I'll give this a try (I thought I already had, but I'll check again).  In any case, I resorted to a different solution:  I use k3b to create the ISO file.  You have to let it "pretend" it's creating a DVD project:


[LIST]
[*]Start K3b with your DVD already loaded in the machine
[*]start "new DVD Data project"
[*]Drag the VIDEO_TS directory into your project
[*]Right click on the VIDEO_TS directory in your project pane and select "Burn."
[*]In the window that opens next, on the first tab, make sure only the "Only Create Image" option is checked.
[*]Go to the "Image" tab and enter a path AND filename for your image, with the extension ".iso"
[*]Start the process.
[/LIST]
In the end, you should have an ISO file in the location you designated.  What I like about this is, that it strips the region code (the last time I tried k9copy, it preserved the region code) -- provided of course you have your CSS libraries installed.

Hope this helps, and thanks for your suggestions as well.

---

### Post by newyorkpaulie on 2009-12-13
Thanks r_a,
And I will give your method a try. BTW, why is region code stripping a plus for you?

---

### Post by r_avital on 2009-12-13
Because I buy DVD's from foreign sources (like Amazon-France) that won't play on US-sold Region-1 players.  Of course, there are region-free DVD players, but they're not cheap, and that's a whole other story anyway :)

(Generally I prefer watching a movie in my living room and not on my computer.  OTOH, I suppose I could rig a real cheap used PC from eBay with Ubuntu, connect it via VGA or HTMI to my tv and play them that way.)

---

### Post by thync on 2010-02-11
Hola, I don't suppose we have a fix for this yet? Although the K3b route works, it is rather a workaround than a fix. I like to keep things simple.

---

