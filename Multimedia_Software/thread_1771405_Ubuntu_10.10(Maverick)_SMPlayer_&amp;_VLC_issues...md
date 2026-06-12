---
title: "Ubuntu 10.10(Maverick) SMPlayer &amp; VLC issues..."
date: 2011-05-30
forum: Multimedia Software
---

### Post by medusa~ on 2011-05-30
1. I use exclusively smplayer and vlc for video playing
2. Suddenly vlc can't play vids anymore. But if u pull `top` or whatever process viewer it shows that its running behind the scene. but acted like didn't even start.
3. Okay, vlc misbehaving, smplayer is well unpredictable. It runs and plays with audio with the video screen being transparent, completely! I mean the video place just shows through to the desktop or whatever window is behind it. I have attached screen shots below.
4. I am using Gnome, nvidia card, been using these apps not until recent they get buggy and having issues. And oh yeah, codecs are in, I install them all and double checked.
5. I am suspecting compiz? Or Metacity compositing feature?

And Finally, Ubuntu is really starting to get buggy! I tried 11.04. I had to run back to 10.10.

---

### Post by medusa~ on 2011-05-30
common, pls  help!

This is my 3rd topic and no one ever provides solution. I always end up solving myself. I have no idea on this one really. Pls give a clue if u hav any!

---

### Post by mc4man on 2011-05-30
For starters I'd - 
open home folder (view > show hidden files) 
in .config delete both the smplayer and vlc folders
in .cache delete the vlc folder
in .local/share delete the vlc  folder

For smplayer try **one** of the below, the first affects smplayer opened from applications menu and r. click, the 2nd all possible uses of smplayer

```
gksudo gedit /usr/share/applications/smplayer.desktop
```

Find the Exec=smplayer %U line, make it look like this
```
Exec=env XLIB_SKIP_ARGB_VISUALS=1 smplayer %U
```

Or - in terminal
```
sudo bash -c "cat > /usr/bin/smplayer.helper" <<EOF
export XLIB_SKIP_ARGB_VISUALS=1
exec smplayer.real "\$@"
EOF

```
then 
```
sudo chmod 755 /usr/bin/smplayer.helper
```
```
sudo mv /usr/bin/smplayer{,.real} && \
sudo ln -sf smplayer.helper /usr/bin/smplayer
```

If doing the latter and it helps - if smplayer is ever updated then just _run the last code box _again

After deleting those folders start vlc from the terminal and see what it says

---

### Post by medusa~ on 2011-05-31
thx for helping. It is partially solved. the idea of clearing config files pricked my mind but didnt wanna. well i didnt have a choice anymore. I did.

VLC is back behaving normal. But refuses to play MKV. I dont know why. thinking codec. but it used to and i just checked on the codec again, its ok.

for SMPlayer, i followed all until the point of 
```
sudo chmod 755 /usr/bin/smplayer.helper
```the file or folder smplayer.helper do not exist on my system. was wondering if to create it and go on with the rest of the instructions.

once more thanks for helping. Still looking for solution.

I did a complete purge of smplayer. "sudo apt-get purge smplayer" then install again. same thing as if I didnt do anything.

---

### Post by mc4man on 2011-05-31
> for SMPlayer, i followed all until the point of ....
Not sure what you mean by all. 
Before running sudo chmod 755 /usr/bin/smplayer.helper you were to run the codebox above that has 4 lines - it's meant to be copied, pasted and run, (enter on keyboard), as one. That would have created smplayer.helper.

You could otherwise try editing the smplayer.desktop as described above the "Or - in terminal" line (open the .desktop and edit the line to look like as shown

---

### Post by medusa~ on 2011-06-01
Jesus, you are a magician! SMPlayer is completely back! It worked like a charm. Sorry i didn't do the or in terminal command box. 

VLC is still struggling with MKV. I ran it from terminal, here is the output

```
medusa@medusa-lair:~$ vlc
VLC media player 1.2.0-git Twoflower (revision exported)
[0x9baa90c] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xa287144] mkv demux error: cannot find KaxSegment
```
Did a little googling on KaxSegment. Having something to do with matroska codec not working well with VLC; I guess. 

I did this from the terminal just to double check, 
```
mplayer -vo gl best\ of\ moment\ 1.mkv
```
I could view it. so I think this problem is VLC specific.

---

### Post by mc4man on 2011-06-01
Vlc has a number of current issues though I'd use the 1.2+ like you're doing, you could search thru the Videolan forum, good luck there...

If you happen to update or re-install smplayer - just to nail down - you'll have to re run the LAST codebox to reset (just the last one - as in 
```
sudo mv /usr/bin/smplayer{,.real} && \
sudo ln -sf smplayer.helper /usr/bin/smplayer
```

---

### Post by medusa~ on 2011-06-01
mc4man, Thank you! Really appreciate your help. I'd say that was genius. I wish i knew a bit of what u did, lolx. This post is just to say 'Thank You!'

I will mark this as solved now!

---

### Post by medusa~ on 2011-06-01
I think Insane troll dropped by...what is that supposed to mean if your don't contribute to making VLC play MKV? :confused:  To make it worst its your first post on this forum :mad:

---

