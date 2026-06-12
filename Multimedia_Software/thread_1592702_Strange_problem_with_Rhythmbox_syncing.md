---
title: "Strange problem with Rhythmbox syncing"
date: 2010-10-10
forum: Multimedia Software
---

### Post by Beastlicker on 2010-10-10
Hey forum, I installed Ubuntu 10.10 today and set it all up. Later, I plug in my iPod Touch 2g running software version 4.0.2. Ubuntu detects it and mounts it and all, so I open Rhythmbox. I add my library into it, and sync it all into my iPod Touch.

When it finishes, I check to make sure the files are shown on the iPod, and they are. When I go to play one of them, strange things occur. When I tap the song, it will show how long the song is at the top and all, then the length of the song time will switch to 0:00 (not the amount of the song I've played) and it will return me back to the previous screen where I chose the song.

This happened with all the **new **songs I synced up to it. Anyone know a fix?

---

### Post by peniop on 2010-10-11
Same problem with a just upgraded ubuntu 10.10 amd-64 and Ipod nano 5th generation...

---

### Post by k1id on 2010-10-11
I'm having the exact same problem songs before upgrading work fine, but new songs I sync won't play on 4th gen nano. Does anyone know why this is happening or how to fix it?

---

### Post by addictedkoala on 2010-10-12
Don't want this thread to die, having a similar problem. When I go to sync half the songs don't work because Rhythmbox tells me they're not in a format compatible with the device, even though I transferred all the songs from my iPod in the first place. The songs that do work don't play though as has been described in the OP.

I'm installing Banshee now just to see if it's a Rhythmbox or an Ubuntu bug

edit: Installed Banshee, couldn't get the program itself to work so forget that. Also turns out the format error was because the files lacked extensions. However the second problem where the iPod gets no track is still there

---

### Post by Aerodynamic on 2010-10-12
Hello, i have the same problem.
I can sync to the iPod without any problem, but when you're trying to play the song with the iPod nothing happens.

There wasn't any problem with Ubuntu 10.04, problem occurred when i installed Ubuntu 10.10

---

### Post by the.ourea on 2010-10-13
bump++

Running Ubuntu 10.10, Rhythmbox 0.13.1.  MP3 files get oddly munged when sent to my Android 2.2 phone via the Rhythmbox GUI.  Manually copying the same files with Nautilus from my file system to the phone works no problem.  Looks like I'll be reverting to Rhythmbox 0.12, bummer.

---

### Post by Aerodynamic on 2010-10-13
Hi, see bug 658085 on [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu).

I recommend you all subscribe to the bug, so they can see it's affecting a lot of people.

This is a serious flaw in rhythmbox..

---

### Post by k1id on 2010-10-13
> **Aerodynamic said:**
> Hi, see bug 658085 on [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu).

I recommend you all subscribe to the bug, so they can see it's affecting a lot of people.

This is a serious flaw in rhythmbox..
Will do. And yes this is very serious. It makes Rhythmbox completely useless to me, while leaving me stuck with the same music on my iPod.

---

### Post by cphayes0914 on 2010-10-15
Ok, heres another problem I got.  Im using an Ipod shuffle 2g.  When I go to sync ANY songs(mp3,m4a,etc) it says it has put the song on the ipod.  when I eject the ipod and try to listen, the green light blinks green and orange(error code) and will not play any songs, even though when I just tried it on windows with itunes, all forms work.  Rhythmbox will read the ipod and see the songs from before, but rhythmbox's syncing puts it out of commission until I restore it.  wonderful.  Im a relative newbie to linux so if Im doing something wrong, please let me know.


Just to throw a stick in the wheel, banshee doesnt want anything to do with my ipod, and I even tried using Kubuntu, getting same funky problems with Amarok.  GTKpod works fine, though it gives me hell about my m4a files.   Ubuntu 10.04 gave me NO grief about this Ipod, just happened with my upgrade to 10.10

---

### Post by kirbatron on 2010-10-15
Having the same problem after a clean install of 10.10. Both my wifes 5g video and my 80 gb classic.

---

### Post by cphayes0914 on 2010-10-15
Im assuming its a 10.10 issue.  Ive tried every ipod managing tool I could get my hands on, seems none take too kindly to my ipod anymore.

---

### Post by r0dr160_n on 2010-10-15
> **cphayes0914 said:**
> Ok, heres another problem I got.  Im using an Ipod shuffle 2g.  When I go to sync ANY songs(mp3,m4a,etc) it says it has put the song on the ipod.  when I eject the ipod and try to listen, the green light blinks green and orange(error code) and will not play any songs, even though when I just tried it on windows with itunes, all forms work.  Rhythmbox will read the ipod and see the songs from before, but rhythmbox's syncing puts it out of commission until I restore it.  wonderful.  Im a relative newbie to linux so if Im doing something wrong, please let me know. 

Same problem here

Using the "Portable players - ipod" plugin, can't copy songs to an ipod shuffle 2nd gen. I select the songs form a playlist and drag them to the ipod icon on the rhythmbox window but does nothing.

Also if I click on the "Sync with library" or the "properties" menu on the ipod icon rhythmbox crashes and closes the window.

Disabling the ipod plugin and enabling the MTP plugin rhythmbox still detects the ipod. This way is possible to copy songs to the ipod but since they're not put on the "iPod_Control/Music" folder, the ipod wont play any song. Here the "properties" menu works just fine.

---

### Post by mabo1 on 2010-10-16
I have the same problem with Rhythmbox and my ipod. All new files I sync since installing 10.10 are not working. I found that the mp3 file extension is missing from the file name on my ipod. Older files that have been on my ipod for a while work ok and they have the file extension.

---

### Post by r0dr160_n on 2010-10-17
I found a not so elegant solution that worked with my iPod Shuffle 2nd generation.

First synchronize the iPod with an iTunes (I used another computer running windows that didn't have the music i wanted on my iPod) but don't put any song.

When the iPod is empty rhythmbox will read it fine and you can add the songs you like. When rhythmbox is done eject and unplug the iPod. If you try to play the songs you'll get a green and orange blinking light which means error or no songs to play.

Then plug the iPod back into the computer that you used to synchronize with iTunes and cancel the synchronization as soon as it starts, otherwise iTunes while erase the songs and you'll have to start again. Once you cancel the synchronization you should be able to see the songs you put using rhythmbox (maybe a few got lost). Now you can unplug the iPod and it should play the songs right.

Like I said, it's not an elegant solution but at least it lets you add the songs you have on your linux computer.

---

### Post by pa0lo87 on 2010-10-20
I have the same problem, too

---

### Post by cphayes0914 on 2010-10-28
Ok, now here we go with the ipod support again.   Now rhythmbox wont even see the songs on my ipod, before it would.  Banshee doesnt see my ipod.   Exaile reads it fine. hrm.   Hipo ipod tool says:

"detected unsupported databse version 51"

then it says:  


  at IPod.DatabaseRecord.Read (IPod.DatabaseRecord db, System.IO.BinaryReader reader) [0x00000] in <filename unknown>:0 
  at IPod.TrackDatabase.Reload (Boolean createFresh) [0x00000] in <filename unknown>:0 
  at IPod.TrackDatabase..ctor (IPod.Device device, Boolean createFresh) [0x00000] in <filename unknown>:0 
  at IPod.Device.LoadTrackDatabase (Boolean createFresh) [0x00000] in <filename unknown>:0 
  at IPod.Device.LoadTrackDatabase () [0x00000] in <filename unknown>:0 
  at IPod.Device.get_TrackDatabase () [0x00000] in <filename unknown>:0 
  at IPod.Device.get_Name () [0x00000] in <filename unknown>:0 
  at IPod.DeviceCombo.AddDevice (IPod.Device device) [0x00000] in <filename unknown>:0 
  at IPod.DeviceCombo..ctor () [0x00000] in <filename unknown>:0 
  at Hipo.HipoMainWindow.CreateWindow (System.String[] args) [0x00000] in <filename unknown>:0 
  at Hipo.HipoMain.Run (System.String[] args) [0x00000] in <filename unknown>:0 
  at Hipo.HipoMain.Main (System.String[] args) [0x00000] in <filename unknown>:0 


Any ideas? 

Id use gtkpod, but gtkpod when I load my ipod shuffle which is a late 2007 model and not even on the list, says .....

"Extended Info Will Not Be Used
iPod database Import Failed: 'iTunesStats file ('/media/VICTORIA'S/iPod_Control/iTunes/iTunesStats'): entry length smaller than expected (0<32)."

Im at a loss, as I dont have the time or computer expertise to figure this out.  Im sure a programmer could tell me whats going on, but alas I am not one.

---

### Post by cphayes0914 on 2010-10-28
Ok, you wont believe this but finally, my ipod shuffle is working with rhythmbox, the way it should.   now I installed banshee, then gtkpod then hipo pod then exaile, then I reinstalled rhythmbox and everything, still nothing.   then installed every gstreamer plugin I could install, still nothing.   finally my ipod stopped working, no kidding.  then it started working again.  well I was cursing the linux gods when I restarted my computer and lo and behold, it works like ubuntu 10.04.   no kidding.   Only thing I can think is that upon restarting, podsleuth, which was never installed to begin with, needed the restart(a dbus issue I believe a post said) or the fact that I reinstalled rhythmbox and podsleuth,  or maybe both.   either way, its working like a charm.  my advice is install podsleuth and possibly reinstall rhythmbox, then try again.  Maybe a linux master could tell me what has been going wrong.

---

### Post by tabuxander on 2010-10-29
try 

sudo apt-get install gstreamer0.10-plugins*

hope this will help..i saw at [http://ubuntuforums.org/showthread.php?t=1600537](http://ubuntuforums.org/showthread.php?t=1600537)

---

### Post by r0dr160_n on 2010-10-30
Didn't work for me :(

---

### Post by peniop on 2010-10-31
> **tabuxander said:**
> try 

sudo apt-get install gstreamer0.10-plugins*

hope this will help..i saw at [http://ubuntuforums.org/showthread.php?t=1600537](http://ubuntuforums.org/showthread.php?t=1600537)


I did work for me... now everything is perfect... thanks a lot :-)))

---

### Post by puyopuyo on 2010-11-19
I have the same problem. I have solved it using gtkpod.

I have formated my ipod shuffle 2gen with itunes, I have removed the directory ~/.gtkpod from my ubuntu, I have connected my ipod to my computer and I have started gtkpod. it can take some times to start and I have transfered music with gtkpod and everything was ok.

at the begining i have start to transfert music with rhythmbox and gtkpod was just used to correct the ipod database but it was not working everytime.

---

### Post by MasterKush010 on 2010-12-04
can't copy songs to an ipod shuffle 2nd gen. I select the songs form a playlist and drag them to the ipod icon on the rhythmbox window but does nothing.

Also if I click on the Sync with library or the properties menu on the ipod icon rhythmbox crashes and closes the window.    HELP !!   Tried  sudo apt-get install gstreamer0.10-plugins*      &  1. Go to your home folder (Places>Home Folder)  2. Press CTRL+H  3. Navigate to .gconf>apps>rhythmbox>state>ipod  4. Delete %gconf.xml file (it will be recreated the next time you start rhythmbox)  5. Restart rhythmbox.     BUT Still no pod :(

---

### Post by Aerodynamic on 2011-01-09
This bug should be fixed if you update 10.10
Had the same problem, but it works now.

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/659244](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/659244)

---

### Post by reptileqc on 2011-05-18
It didn't work for me and I saw a lot of different posts regarding fresh installs of 10.10 with no success.

I just posted a long post with one of many possible solutions for those not wanting to wait for an update. ;)

[http://ubuntuforums.org/showthread.php?p=10830193#post10830193]("http://ubuntuforums.org/showthread.php?p=10830193#post10830193")

Hope this helps.

reptileqc

---

