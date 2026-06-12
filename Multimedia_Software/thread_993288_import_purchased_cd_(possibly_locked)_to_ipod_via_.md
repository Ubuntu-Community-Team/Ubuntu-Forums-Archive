---
title: "import purchased cd (possibly locked) to ipod: via rythmbox/floola"
date: 2008-11-25
forum: Multimedia Software
---

### Post by WaNaBePi on 2008-11-25
hahaha it took me so long to write this that i was logged out;)

OK so i bought a new album, just to satisfy your possible curiosity its the killers, day and age album

so maybe if it wasn't so poppy it would work!

in any case the files on the cd are locked there is a orange picture of a padlock, all the files on the cd are .wav files when i browse though the cd with the ubuntu file browser

(Uncompressed 16-bit PCM...WAV audio (audio/x-wav) this is the info i get when i open the properties of the file this is track 1. (i doubt they are different as the tracks progress)

not until i plugged into the Internet did the cd even play in rythmbox or totem. rythmbox retrieved the info for the cd and i was able to at least play it (after the Internet was plugged in)

as the title of the post says, i want to put these files on my ipod, however ive never added files from a cd (purchaed from a store) onto my ipod using ubuntu or rythmbox etc. ive been playing with rythmbox and totem and brasero for a while to see if i can get it. and i read up on .wav files on wikipedia didnt help.

i get this error when i try to extract the songs to my hard drive(the computer hd) through rythmbox>(that menu on the left that you navigate with)>devices>"day and age" while the cd is selected there is the extract icon and i hit it it seems to do a whole bunch of work (like its going to work fine no problems) and i get a error for every track "GStreamer encountered a general stream error" if i copy the cd which i did successfully using brasero>new project>"disc copy"(but the menu calls it copy disk(weird, different names...)) it copies all the locks and tracks, rightfully so. so it is an exact copy... i tried this cause in itunes if you make a cd with the acc files from itunes, and then re-import that burned cd you can get them converted as mp3s if you have cds selected to import that way so i was trying to do something similar, i may end up trying that if i cant get this to work soon but im so ethicaly opposed to the windows/apple corporate capitalism stuff, so ill wait, moreover that doesn't help me learn ubuntu or any of its accompanying software :) 

but i cant get this cd on my ipod and thats what i want to do i want this album on my ipod with all the track info, and in 320 kbps mp3 how????????????????????????

i keep all my music on my ipod and a external hd, and ide like to do the same for this cd. and just for clarification i use floola  but i guess it works through rythmbox as i understand it where as on windows it was a stand alone program.


i hope ive given the right info to be helped please let me help you help me ill keep my eyes on this post feel free to private message me im very frustrated over this... 

the conspiracy theorist in me says that the producders put some heavy file proection on this album so thats why im having this difficulty 

oh and i have one other .wav file on my iopd and according to the properties window its the same type to the "T" sooooo yea even more perplexing...

HeLp? thanks.

---

### Post by WaNaBePi on 2008-11-26
so sorry to bump... why is there, to me, seemingly that there is so little .wav support in ubuntu..... i thought .wav was fairly common as a audio file format guess i was wrong

im gonna try looking for a file converter to change my .wav into .mp3 

ill be around if anyone has any good programs for file conversion to recommend.

---

### Post by WaNaBePi on 2008-11-26
well problem solved... i just broke down and used windows(floola works well there)...yuck i feel dirty...

but i see it like this: all operating systems SUCK 

lunix can do so mmany great things make software, hack, crack, and mak on chicks by cyber-stalking them(joking) but there is little ability to anything simple...

windows sucks it can only do simple things like syncing ipods if you actually want to USE your computer, you cant. you are stuck to what windows wants you to do, the same goes for apple

at THIS point i think its only realistic to have both ubuntu and windows on ones computer, if you would like the most potential on your computer, sadly. 

i wish more people wouldn't be so scared to try something different. because if Linux were more popular there would be more reason for more developers to make truly flawless software... but that would give rise to linux viruses and things of that sort, no big deal i suppose... but oh, one day ;)  

but really rhythmbox/floola needs to manage ipods better if it did it would be a good selling point to make others want to try ubuntu out

is there a better combo out there that anyone has heard of, or better yet uses, than rhythmbox/floola......PLEASE TELL ME


GOD, WAY TO TALK TO YOURSELF, LOOSER! 

later guys and girls

---

### Post by WaNaBePi on 2008-11-28
to continue talking to my self there is a terminal ?code? ?script? that must be run before one can double click on the floola icon in ones ipod to work the code is at the "floola.com" web site if you select the Linux version of the software

the code:   sudo apt-get install libnotify-bin

then this didn't work at fist, so i looked around and found this one
entered it also in the terminal and it worked!!!!!!!!! yay go linux!!!!! 

the code: sudo apt-get install libstdc++5

"Installation, Linux

Floola relies on libstdc++5. To install it (under Ubuntu) type sudo apt-get install libstdc++5 via terminal. To enable playback you'll need either gstreamer or lib xine to be installed. If both are installed gstreamer will be used.

To start Floola, just double click on application icon or from console type ./Floola. If it still doesn't start, make sure it has correct permissions typing chmod +x Floola via terminal from the folder where you extracted Floola."([http://www.floola.com/modules/wiwimod/index.php?page=docs_install](http://www.floola.com/modules/wiwimod/index.php?page=docs_install))

hope this helps any one with similar problems

there is a youtube video that helps as well look up on there(youtube) "floola ubuntu install"... yada yada

yes im still having fun talking to my self!

---

