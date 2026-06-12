---
title: "Banshee + ipod classic"
date: 2008-06-19
forum: Multimedia Software
---

### Post by PsychedelicReaction on 2008-06-19
Hi guys, i use banshee 1.0 and it recognize fine my ipod classic. when i try to  transfer files from pc to ipod, banshee screws up itunes database. in fact when i turn on the device it says that there isn't any music or video file, i need to correct all the errors with gtk pod. i couldn't find any solution or guide on internet. somoeone can help me?

---

### Post by cozmicharlie on 2008-06-19
This might help - [http://sofabedz.co.uk/linux/iPod.html#Hardy](http://sofabedz.co.uk/linux/iPod.html#Hardy)

---

### Post by PsychedelicReaction on 2008-06-19
mmh thanx but i already did it, i double checked information in that files and seems corrected.
in my case (iPod Classic Black):
> ModelNumStr: xB147
FirewireGuid: 000A270015454BEF

---

### Post by cozmicharlie on 2008-06-19
Do you have podsleuth installed?

---

### Post by PsychedelicReaction on 2008-06-20
yes, it is installed

---

### Post by cozmicharlie on 2008-06-20
Do the music files display in Banshee when you have your ipod hooked up?  Are you adding mp3's?

I use Banshee but not for my ipod.  I installed Rockbox on my ipod (much better,) mainly so I can play flac files.  I still have the itunes loaded on it though so I will play around with it in Banshee today and see if I can come up with something that will help you.

---

### Post by PsychedelicReaction on 2008-06-20
Here's what happens:

1. I connect my ipod classic and it is recognized fine by Banshee, it can play mp3s directly from the device
2. I drag an album from my library and i drop it in the ipod, mp3s are added correctly and i can play them with banshee from the device
3. I eject the ipod from banshee and when i turn it on it says "No music"
4. I connect again the ipod to the pc and i open gtkpod that gives me an alert (it's in italian so i give you my personal translation  :))
> 
iTunesDB «/media/ILUV/iPod_Control/iTunes/iTunesDB» has a checksum different from the one in the file with the extended informations «/media/ILUV/iPod_Control/iTunes/iTunesDB.ext»
 gtkpod is trying to compare this information with the SHA1 checksum. This will require some minutes.
Then it procedes with the scan and fortunately it recovers my ipod.

I would like to try rockbox but it doesn't work with the latest generation :(

---

### Post by cozmicharlie on 2008-06-20
> **PsychedelicReaction said:**
> Here's what happens:

Then it procedes with the scan and fortunately it recovers my ipod.

I would like to try rockbox but it doesn't work with the latest generation :(
 When you say it recovers - does it show the music you added in Banshee or does it revert back to the state before you added the music in Banshee?

They will soon come out with a new Rockbox version hopefully.

---

### Post by PsychedelicReaction on 2008-06-20
yes, it recovers music added with banshee too

---

### Post by cozmicharlie on 2008-06-20
I did a little digging around in the Banshee forums and this might be a bug in Banshee ([http://bugzilla.gnome.org/show_bug.cgi?id=536741](http://bugzilla.gnome.org/show_bug.cgi?id=536741)).  Indeed, someone just posted with the same problem.  You may want to monitor the Banshee forums to see if someone responds. Sorry, I could not help you solve the problem.

---

