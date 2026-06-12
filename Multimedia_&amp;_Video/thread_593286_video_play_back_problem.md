---
title: "video play back problem"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by Angelbeast on 2007-10-27
I'm not exactly sure when this started. It was sometime right after i upgraded to Gutsy. Now when i play back some videos in Totem with deinterlace UNchecked which is how i always watched them there is a large green or blue colored band at the top of the screen...when i check deinterlace it goes away but that way the picture is not very sharp and there are blurry bands on all sides of the picture...any help? thanks in advance ...

---

### Post by Angelbeast on 2007-10-29
*bump bump bump*

NO ONE has any ideas at all?

---

### Post by rumli on 2007-11-04
If you are using totem-xine, try [this]("http://ubuntuforums.org/showpost.php?p=3706935&postcount=2").

---

### Post by Angelbeast on 2007-11-04
> **rumli said:**
> If you are using totem-xine, try [this]("http://ubuntuforums.org/showpost.php?p=3706935&postcount=2").

Thank you for the response...i tried to change the file but it keeps resetting when i restart...Here is what i have...

this is the originl setting

# video driver to use
# string, default: auto
#video.driver:auto

I change it to

# video driver to use
# string, default: auto
#video.driver:OpenGL

do i need to change the setting above that to OpenGL also so it doesn't reset?

---

### Post by rumli on 2007-11-04
You need to drop the "#" character from the start of the line.

That is, make it:
```
video.driver:OpenGL
```
instead of:
```
#video.driver:OpenGL
```

The "#" character means the line is commented out (i.e., ignored), and so Totem feels free to "clean" it up and change it back to the default comment whenever it runs.

---

### Post by Angelbeast on 2007-11-04
> **rumli said:**
> You need to drop the "#" character from the start of the line.

That is, make it:
```
video.driver:OpenGL
```
instead of:
```
#video.driver:OpenGL
```

The "#" character means the line is commented out (i.e., ignored), and so Totem feels free to "clean" it up and change it back to the default comment whenever it runs.

alright well i have no clue what i'm doing wrong here but it keeps resetting...I even tried taking the "#" off of the line above it too and setting both of them to OpenGL and even that didn't work...do i need to do this s root or something?

---

### Post by rumli on 2007-11-04
Don't need to do this as root, and don't remove the # from the line above it.

First, make sure Totem is closed.  Then edit the file, and make sure the video.driver section looks like this:
```

# video driver to use
# string, default: auto
video.driver:OpenGL
```
Then save and close the file.  Then open totem and use it as usual.

---

### Post by Angelbeast on 2007-11-04
> **rumli said:**
> Don't need to do this as root, and don't remove the # from the line above it.

First, make sure Totem is closed.  Then edit the file, and make sure the video.driver section looks like this:
```

# video driver to use
# string, default: auto
video.driver:OpenGL
```
Then save and close the file.  Then open totem and use it as usual.

Now it's working but do i have to do this each time? Or should it be saving like that when i restart?

---

### Post by rumli on 2007-11-04
You don't have to do anything further.  It should work from now on even after you restart.

---

### Post by Angelbeast on 2007-11-04
> **rumli said:**
> You don't have to do anything further.  It should work from now on even after you restart.

Okay...before it would reset when i retsrtaed but i was thinking i put a space where the "#" was that i removed...would that be why it wouldn't save?

---

### Post by rumli on 2007-11-04
> **Angelbeast said:**
> Okay...before it would reset when i retsrtaed but i was thinking i put a space where the "#" was that i removed...would that be why it wouldn't save?

Yes, I just tried it out, and I found that the space does indeed make it reset.

---

### Post by Angelbeast on 2007-11-04
> **rumli said:**
> Yes, I just tried it out, and I found that the space does indeed make it reset.

Ahhhh...okay then i guess i AM all set *LOL* ... thanks allot for your help  :-)

---

