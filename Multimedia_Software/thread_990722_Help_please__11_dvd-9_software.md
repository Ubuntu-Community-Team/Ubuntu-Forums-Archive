---
title: "Help please:  1:1 dvd-9 software"
date: 2008-11-23
forum: Multimedia Software
---

### Post by Black Razor on 2008-11-23
Ok, I am past patience.  Someone please help me figure out how to make a backup copy a DVD-9 disc in Ubuntu.  Brasero and K9Copy do NOT work.  Please, and stress my plea, PLEASE do not give me some command line instructions because I just refuse to use CLI for DVD authoring. Someone please save me from having to go back to windows.  I want to make 1:1 backups of DVD-9 discs.  I AM NOT going to compress anything.

---

### Post by zander1013 on 2008-11-23
do you have libdvdcss2 installed?

---

### Post by Black Razor on 2008-11-23
::blinks:: .....yes.

---

### Post by Twitch6000 on 2008-11-23
If I am right on windows,dvd shrink along with DVD Decrypter would be used to do this.

If so download wine and use dvd shrink >.>.

According to the appdldb it runs just fine.

---

### Post by mc4man on 2008-11-23
What is your intention for your backups, are you just saving to hdd or plan on playing from hdd or to burn to dvd-dl media?

---

### Post by Black Razor on 2008-11-23
Dude, what part of 1:1 ratio didn't you get?

---

### Post by Black Razor on 2008-11-23
You know what, I dont know why I keep torturing myself.  I've spent over ten years working with Windows, even DOS and Win 3.1    Why I ever thought I could be happy with Linux is beyond me.  Screw this ******** I'm going back to my native environment which I know inside and out down to every single nut and bolt.  I don't need these damn headaches every time I try to do something.   Have fun everyone, but Linux (servers aside) is just NOT for me.	](*,)

---

### Post by mc4man on 2008-11-23
If you knew it inside and out you'd know that a 1:1 copy has nothing to do with
 > .... for DVD authoring.

It's just ripping, period, no authoring involved.

cya

---

### Post by zander1013 on 2008-11-23
> **Black Razor said:**
> You know what, I dont know why I keep torturing myself.  I've spent over ten years working with Windows, even DOS and Win 3.1    Why I ever thought I could be happy with Linux is beyond me.  Screw this ******** I'm going back to my native environment which I know inside and out down to every single nut and bolt.  I don't need these damn headaches every time I try to do something.   Have fun everyone, but Linux (servers aside) is just NOT for me.	](*,)

try brasero under Applications->Sound&Video.:(

---

### Post by bigbrovar on 2008-11-23
i have never dissed anyone on the forum before .. but this is the closest i would get.

good riddance. because honestly we dont need people like you here.. coming demanding help has if u deserve it. FYI. nobody here is paid to give help or support. we all do it out of the kindness in our heart. just like the great pple that made ubuntu,linux and the wonderful tools that made it all work. they is a culture in free software.. and that culture is guided by respect. which u lack. go and never come back. if u decide to use windows believe be i cant wish u a better punishment. lol

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-23
> **Black Razor said:**
> You know what, I dont know why I keep torturing myself.  I've spent over ten years working with Windows, even DOS and Win 3.1    Why I ever thought I could be happy with Linux is beyond me.  Screw this ******** I'm going back to my native environment which I know inside and out down to every single nut and bolt.  I don't need these damn headaches every time I try to do something.   Have fun everyone, but Linux (servers aside) is just NOT for me.	](*,)

man you must be haveing a bad day

looked at most of your other post you dont normally get this pissed
just clam down. 

Have fun with windows, bye and if you come back thats ok 2

---

### Post by Black Razor on 2008-11-23
Yea I was having a bad day.  You are correct...I'm normally very level headed.  I had a huge fight with my spouse earlier in the day and I guess I was projecting.  I apologize to everyone, and I hope you'll forgive me.

Now, for my problem.  I need to copy 1:1 ratio DVD-9 movies to DVD-DL media.  I don't want to use compression, I want a 1:1 copy.  I do have DeCSS installed and the other two codecs for DVD playback.  That's not the problem.

My problem is the layer break.  I can extract the ISO with k9copy no problem.  My problem is I don't have software that can burn the layer break successfully.

Anyone?  The easier the better, because I am not motivated to go to extreme measures for a dvd backup.  I should define extreme by uncessarily complicated procedures.  I'm a GUI fan, not a CLI fan.  If you have some easy CLI commands then I'd be willing to give it a try.

What's very important is it needs to be a clone, not a extracted burn.  I'm trying to back up my very expensive TV collection.  It's really important for me to have the entire directory structure and menus intact.

---

### Post by mc4man on 2008-11-23
If you can't find something else suitable, don't mind using wine, and *spending a little time getting used to using*, then Imgburn will do perfect Dl burns. (over 70 done, none bad.
 It also will show you all the available layer break choices, rate them for you as to suitability , and allow you to preview the actual layer break in a video window first.

Important - the layer break is created in making the iso, not afterwards.

So Imgburn needs to create it for you. Better to have k9 just create a folder, not the iso. If it does create the iso, the folder is available in /tmp till you close or rerun k9 again. 

Or you can let it start creating the iso, cancel and go grab the folder.

It's very easy to set up, let me know if some help. The defaults are good except for the io/interface which should be set to first option.

See screens

[http://www.imgburn.com/](http://www.imgburn.com/)

Some good guides and active forum also

Small note : the author of Imgburn is lightning uk (creator of the now defunct DVD Decrypter - thanks to macrovision and sony

final note: what dl media are you using? Verbatium is superior

---

