---
title: "how to play WMV files on ubuntu"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by wolfgang959 on 2007-05-03
hi 

i am an edgy user and i have found some video tut's on the internet for download. so i downloaded them but i couldn't get them to play because they were WMV files.

any help on being able to play these. 

thanks:)

---

### Post by Rashid584 on 2007-05-03
Open Add/Remove applications and select "all" from the drop down menu, then type ubuntu-restricted and download the package(s) that come up.

I think that should work...lemme know if it doesn't 

-Rashid

---

### Post by wolfgang959 on 2007-05-03
no sorry 

when i typed it and searched for it nothing came up

thanks:)

---

### Post by Rashid584 on 2007-05-03
Do you have universe and multiverse repositories enabled?

-Rashid

---

### Post by wolfgang959 on 2007-05-04
how do i enable those repositories.

thanks
:)

---

### Post by BabyUbuntu on 2007-05-04
open add/remove Applications... click sound & video.. than u downlod GStreamer.. its work for me

---

### Post by wolfgang959 on 2007-05-04
i have downloaded the gstreamer files but totem says 'could not determine the type of stream'

---

### Post by wolfgang959 on 2007-05-04
i have just tried it again and now it says 

You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

what do i do now

thanks

---

### Post by YoG%*@ on 2007-05-04
hi there!

first: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")
concerning adding the multiverse/etc repositories. (if you haven't managed to do it yet).
second: try installing mplayer or vlc. they play almost everything...

hth,
mux

---

### Post by spatterlight on 2007-05-04
There's a small magic program called Easyubuntu that sets you up with the appropriate codecs to play all sorts of audio and video files, including wmv files. You can get it from here:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

After you download Easyubuntu and save it to your desktop, you need to open up your terminal: you find the terminal by going to the Applications menu at the top left of your screen. It's in the Accessories folder. Copy and paste the following command into the terminal (this is necessary because it gives Easyubuntu permission to download from the specific servers it needs), then hit return:

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

Then close the terminal and open Easyubuntu. Follow the prompts on the screen to install it. When it's installed, it should be in the Applications menu, under System Tools. Open it from there -- it'll give you a bunch of options as to the programs it can install for you. What you want is to check the boxes "Free Codecs" and "Binary Codecs", then hit OK.

That should enable you to watch and listen to everything you need. You can use Easyubuntu to install a bunch of other great stuff, too... play around with it.

Martin

---

### Post by Akt on 2007-06-13
I did this, applied 14 files.  Still cannot watch WMV files.  Help please!!!

---

### Post by violin on 2007-06-13
try Automatix it worked for me


cheers

---

### Post by Skyriver on 2007-06-13
If you have installed the appropriate codecs and if vlc does not play it then it is probably Microsoft's new vc1 codec. I do not believe there is a way to play this in linux yet, but someone else can verify.

---

### Post by RomeReactor on 2007-06-13
HI. Akt, do you have **w32codecs** installed? If you're not sure, search for them in Synaptic; if they're not there, try [this]("http://ubuntuforums.org/showpost.php?p=2727375&postcount=3").

---

