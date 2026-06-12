---
title: "smplayer has no screen"
date: 2010-12-04
forum: Multimedia Software
---

### Post by beew on 2010-12-04
Hi,

I am having a problem with smplayer. When it opens it has a transparent screen and wouldn't play any video, the audio is however ok.

Please help, thanks.

---

### Post by beew on 2010-12-04
Bump!

---

### Post by beew on 2010-12-05
Nobody has experienced this problem?? I installed SMplayer on two computers with maverick and one with Lucid and the same problem happens in all of them. Am I really that lucky???

---

### Post by SeijiSensei on 2010-12-05
Is this true for all files?  Sometimes a file is corrupted and won't display.  Try another file; do you get the same blank screen?

Look under Options > View Logs to get more information about what the problem might be.

Another problem might be that you've selected a video output option that your machine doesn't support.  Try selecting "xv" from the drop-down list in Options > Preferences > General Video.

---

### Post by beew on 2010-12-05
Hello??!! Anyone? Echo...

---

### Post by beew on 2010-12-05
> **SeijiSensei said:**
> Is this true for all files?  Sometimes a file is corrupted and won't display.  Try another file; do you get the same blank screen?

Look under Options > View Logs to get more information about what the problem might be.

Another problem might be that you've selected a video output option that your machine doesn't support.  Try selecting "xv" from the drop-down list in Options > Preferences > General Video.

Thanks!!!! Finally someone answered my post, I appreciate it even if it doesn't work.

Actually it happens even without any file. When I click smplayer a transparent screen shows up, this should not be the case. There should be a black screen with the smplayer in the middle.

If I try to play a video (have tried mp4 and avi) there is no video, only sound. I will check the options when I go home, but I think output has already been set to xv.

Thanks again man, just for the reply.:P

---

### Post by andrew.46 on 2010-12-05
Hi beew,

Try the following:

```
export XLIB_SKIP_ARGB_VISUALS=1 && smplayer &
```

and if this successful have a read here:

[http://smplayer.berlios.de/forums/viewtopic.php?id=979](http://smplayer.berlios.de/forums/viewtopic.php?id=979)

Andrew

---

### Post by beew on 2010-12-05
> **andrew.46 said:**
> Hi beew,

Try the following:

```
export XLIB_SKIP_ARGB_VISUALS=1 && smplayer &
```and if this successful have a read here:

[http://smplayer.berlios.de/forums/viewtopic.php?id=979](http://smplayer.berlios.de/forums/viewtopic.php?id=979)

Andrew
Hi, 

This works! But do I have to start SMplayer from the terminal and type the same line everytime I use it? I read the link, but I don't think it is a cairo dock or qt prpblem because the problem persists after killing cairo-dock and unlike what a poster said in the link, vlc never has the problem.

---

### Post by andrew.46 on 2010-12-05
Hi beew,

Indeed I do not fully comprehend what is going on there, but if that works you could follow gafjon's fix in post 4 of that thread and then you can start SMPlayer in the usual way. I have not tested this fix myself I will admit...

Andrew

---

### Post by beew on 2010-12-06
Hi Andrew,

Thanks a lot.gafjon's fix works. Now I just want someone knowlegeable to explain to me what the meaning of these codes is
```
 sudo bash -c "cat > /usr/bin/smplayer.helper" <<EOF
export XLIB_SKIP_ARGB_VISUALS=1
exec smplayer.real "\$@"
EOF

sudo chmod 755 /usr/bin/smplayer.helper
sudo mv /usr/bin/smplayer{,.real}
sudo ln -sf smplayer.helper /usr/bin/smplayer 

```

Shouldn't waste a learning opportunity. :)

Again  thanks sooo much for solving my problem!

---

### Post by andrew.46 on 2010-12-06
Hi beew,

> **beew said:**
> Again  thanks sooo much for solving my problem!

Good to hear it is all working although of course the credit belongs to the good folks on the SMPlayer forums :).

Andrew

---

