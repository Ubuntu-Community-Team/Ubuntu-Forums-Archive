---
title: "Unsolvable Sound Problem"
date: 2010-05-01
forum: Multimedia Software
---

### Post by chris3030 on 2010-05-01
A brief background:  I am a former Gutsy and Hardy user that loved ubuntu, but at that point it just wasn't ready so I went back to windows and recently came back to ubuntu with Karmic.  I had been having some sound problems with Karmic (see my previous thread regarding this: [http://ubuntuforums.org/showthread.php?t=1446162](http://ubuntuforums.org/showthread.php?t=1446162)).

I have tried almost everything possible to solve this..every possible fix and guide out there regarding pulseaudio, ALSA, etc with no success.  I have searched this site as well as google exhaustively and I was unable to fix the problems and get the sound workable in Karmic so to spare my sanity, I decided to put it off until Lucid came out.

Lucid is here and I am still having the same problems.  To sum it up they are as follows:

[LIST]
[*]MP3s will play for maybe 30-45 seconds before I hear silence then the rest of the songs will automatically fast forward with no sound.  On occasion, it will not cut out but the sound will skip and sound all garbled. 
[*]Video files will rarely play.  They will play with VLC however with similar results to the MP3s (the sound will cut out after a certain amount of time).
[*]The sound on online videos will only work about 20% of the time using Chrome and about 40% of the time using Firefox.  When the sound does work, once again it is only for a limited time before cutting out.
[/LIST]

To clarify a few things, I have installed the restricted extras package and all of the gstreamer packages.  As I stated earlier I have researched this exhaustively and have tried every fix that I could come across all over the internet with no success.

I really want this to be fixed so I can have a fully functioning computer without having to go back to windows.  Ubuntu is just so awesome to use and I'd like to continue to use it so I am begging for any experts out there to help me fix this.

---

### Post by chris3030 on 2010-05-02
bump

---

### Post by mbuller10 on 2010-05-02
I'm also having lots of sound skipping issues

---

### Post by chris3030 on 2010-05-02
I feel your pain mbuller.  I just can't understand why everything else can work perfectly for me but something as simple and basic functioning as sound just does not want to work no matter what I try.  When I used to run Gutsy and Hardy, sound worked right out of the box.  I've also ran XP on this machine with no sound problems whatsoever so I know its not a hardware issue.  I am pulling my hair out over this.

---

### Post by lidex on 2010-05-02
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by CJ_Hudson on 2010-05-02
Your icon is Kenny Linux Ubuntu penguin, Right?
That cracks me up.
By the way I have sound issues too:- It's very quiet through the USB headphones.

---

### Post by chris3030 on 2010-05-02
> **lidex said:**
> Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

I have downloaded the file to my user folder however I get the following when I run the sudo command:

sudo bash utils_alsa-info.sh
bash: utils_alsa-info.sh: No such file or directory

---

### Post by lidex on 2010-05-02
```
sudo updatedb
locate utils_alsa-info.sh
```

---

