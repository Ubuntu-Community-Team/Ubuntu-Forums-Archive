---
title: "&quot;Deleted stale lock file...&quot; XaraLX wont open"
date: 2010-06-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by GARoss on 2010-06-14
Xara installs but errors when opening with *Deleted stale lock file '/home/george/.XARA-XTREME-WX-xaralx-george* error message. Also, I get the *...cannot find ImageMagick version 6.0.0* but that's normal until it opens the 1st time. Anyways, any clue what *Deleted stale lock file* error means?:confused:

---

### Post by cariboo on 2010-06-14
That seems to be normal behavior, see [this]("http://www.talkgraphics.com/showpost.php?p=228362&postcount=3") post.

---

### Post by GARoss on 2010-06-14
cariboo907
First, let me say I'm very aware that this is Alpha 1 & I'm only working with programs that I'm familiar with to help trouble shoot what works & what doesn't. XaraLx works great on 10.04 LTS.
Anyway I did delete the *.XARA-XTREME-WX-xaralx-george* file & no more error on startup of Xaralx (although it does re-create another one at Xara start-up but no on screen error). Now the ImageMagick error will not go way. I checked & I do have the required ImageMagick-6.0.0 or better. v6.5.7 to be exact. I copied information when using the terminal to launch xaralx below;

[I]george@george-desktop:~$ xaralx

Gdk-ERROR **: The program 'xaralx' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 2324 error_code 8 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
aborting...
Trace/breakpoint trap
george@george-desktop:~$[/I] 

Can this be traced to the root cause?

---

### Post by MacUntu on 2010-06-14
Try ```
XLIB_SKIP_ARGB_VISUALS=1 xaralx
```

---

### Post by cariboo on 2010-06-14
It's a csd (client side decoration) error, I started getting the same thing with grsync yesterday.

---

### Post by GARoss on 2010-06-14
> **MacUntu said:**
> Try ```
XLIB_SKIP_ARGB_VISUALS=1 xaralx
```

I haven't a clue but this works. But, only from the terminal; not from *Applications/Graphics/XaraLx*. Everything seems to work in Xara. Here's a printout from the terminal. What is this doing to make Xara launch that can't be done from *Applications/Graphics/XaraLx*?

[I]george@george-desktop:~$ XLIB_SKIP_ARGB_VISUALS=1 xaralx

(xaralx:2129): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:2129): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:2129): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:2129): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:2129): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:2129): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
george@george-desktop:~$[/I]

---

### Post by mc4man on 2010-06-14
Not really up on the diff. between RGBA (ARGB) and RGB other than the basic's - you can search out easily.
Until fixed many apps won't start by default, whether there will be a 'global' fix or it's up to each app not sure - would lean towards each app.

(I would think most apps that use wxWidgets would be affected.

As far as launching from the menu, there are a couple of ways to 'fix', for xaralx I'd just do this
```
alacarte
```

Then in the properties of Xara Xtreme -> command use this instead
```
env XLIB_SKIP_ARGB_VISUALS=1 xaralx %F
```

Pretty much any affected app can be run from menu as such - I've also created some small scripts in ~/bin to be used as new launch commands  for use from the r. click on a file or folder, ect. or from main menu.
(useful for banshee, muinshee, inkscape, totem-xine ect.

Ex ( using export - for loading files or dir.' from r. click

#!/bin/bash
export  XLIB_SKIP_ARGB_VISUALS=1
totem-xine "$1"

---

### Post by MacUntu on 2010-06-15
CSD should better be worth all that trouble.

---

### Post by GARoss on 2010-06-15
> **mc4man said:**
> 
As far as launching from the menu, there are a couple of ways to 'fix', for xaralx I'd just do this
```
alacarte
```

Then in the properties of Xara Xtreme -> command use this instead
```
env XLIB_SKIP_ARGB_VISUALS=1 xaralx %F
```


OK. Launch from *Applications/Graphics/Xara* works with this fix.
Just curious, as I am not computer-code literate, but is the cause of this issue because Alpha 1's purpose is to focus testing newer OS goals so functional support data needed for software like Xara is omitted & to be added as full launch approaches? In other words, just the essentials are included. Thanks.

---

### Post by rayraven on 2010-06-15
Why people are still using xaralx is beyond me, it hasnt been updated since 2006 iirc and seems to be abandonded. Why use it instead of, say inkscape?

---

### Post by GARoss on 2010-06-15
> **rayraven said:**
> Why people are still using xaralx is beyond me, it hasnt been updated since 2006 iirc and seems to be abandonded. Why use it instead of, say inkscape?

It is abandoned & Xara could care less. Other Linux OS have dumped Xara & maybe it's time Ubuntu did, too. 
As to why, I got used to using Xara back in my Windows days & still like it. Too bad they quit developing it for Linux. I don't use this type of software much anymore & haven't looked at Inkscape. So, what can be done in Inkscape that can't be done in Xara?

---

### Post by rayraven on 2010-06-16
> **GARoss said:**
> It is abandoned & Xara could care less. Other Linux OS have dumped Xara & maybe it's time Ubuntu did, too. 
As to why, I got used to using Xara back in my Windows days & still like it. Too bad they quit developing it for Linux. I don't use this type of software much anymore & haven't looked at Inkscape. So, what can be done in Inkscape that can't be done in Xara?

The question you should be asking is, what cant be done in inkscape that can be done in Xara.

Why? Because the former is actively developed, while the latter is almost a relic.

Regards,
rat

---

### Post by GARoss on 2010-06-16
So, Inkscape is actively developed & is as good as the old relic, Xara? Hardly a reason to change when there's nothing to gain, is there? When Xara's gone I'll take a look. Thanks. ;)

---

### Post by rayraven on 2010-06-16
> **GARoss said:**
> So, Inkscape is actively developed & is as good as the old relic, Xara? Hardly a reason to change when there's nothing to gain, is there? When Xara's gone I'll take a look. Thanks. ;)

That's a good one :p

---

### Post by GARoss on 2010-06-16
> **rayraven said:**
> That's a good one :p
And, per your suggestion I did download Inkscape. It didn't have launch issues like Xara did (& Xara still does without the fix listed in an earlier post) & does appear to offer some 3D effects which XaraLx doesn't (at least I've never found 3D effects in Xaralx). The interface looks similar, too. Worth looking over. Thanks! :smile:

---

### Post by MidBSD on 2010-06-16
I used to use Xara exclusively due to it's speed and ease of use but since moving over to Linux a few years ago, I've been using Inkscape. It's every bit as good as Xara and I don't miss Xara at all now.

I believe they created an Open Source version so that the community could help develop features and fix bugs (that was their intent) but when no-one did, they gave up.

Unfortunately for them, they misunderstood the Open Source community and kept the core engine under lock and key. This is what kept the community from jumping on Xara so everyone flocked to Sodopodi/Inkscape instead.

I'm not sure if they're still scratching their heads wondering why XaraLX didn't take off...

---

### Post by rayraven on 2010-06-16
> **GARoss said:**
> And, per your suggestion I did download Inkscape. It didn't have launch issues like Xara did (& Xara still does without the fix listed in an earlier post) & does appear to offer some 3D effects which XaraLx doesn't (at least I've never found 3D effects in Xaralx). The interface looks similar, too. Worth looking over. Thanks! :smile:

Glad i could help :)

---

### Post by GARoss on 2010-06-18
> **MidBSD said:**
> I used to use Xara exclusively due to it's speed and ease of use but since moving over to Linux a few years ago, I've been using Inkscape. It's every bit as good as Xara and I don't miss Xara at all now.

I believe they created an Open Source version so that the community could help develop features and fix bugs (that was their intent) but when no-one did, they gave up.

Unfortunately for them, they misunderstood the Open Source community and kept the core engine under lock and key. This is what kept the community from jumping on Xara so everyone flocked to Sodopodi/Inkscape instead.

I'm not sure if they're still scratching their heads wondering why XaraLX didn't take off...

I was excited when I first started using Linux that Xara was available. Personally, I think their newer versions are unbeatable but are, unfortunately, Windows only & I haven't been able to get the trialware to work using Wine. I'll never use Windows again so purchasing is not an option.
I recently installed Inkscape but haven't worked with it. I find working with new software frustrating but you get used to it. It appears to have some 3D which Xaralx doesn't & that's a +.

---

### Post by ScislaC on 2010-06-20
GARoss,

One of our core Inkscape developers was a former Xara user, so a number of things were influenced by that. Hopefully it won't be too hard of a transition. Please know that we're always open to suggestions and do what we can to make the user experience as good as possible. Also, Inkscape 0.48 should be final in the near future, so it will land in Maverick (lots of text related improvements, among a rewritten node tool, a new Spray tool, and much more).

---

### Post by GARoss on 2010-06-23
> **ScislaC said:**
> GARoss,

One of our core Inkscape developers was a former Xara user, so a number of things were influenced by that. Hopefully it won't be too hard of a transition. Please know that we're always open to suggestions and do what we can to make the user experience as good as possible. Also, Inkscape 0.48 should be final in the near future, so it will land in Maverick (lots of text related improvements, among a rewritten node tool, a new Spray tool, and much more).
Learning new software can be a real headache. I have found a forum for Inkscape [*http://www.inkscapeforum.com/viewforum.php?f=6*](*http://www.inkscapeforum.com/viewforum.php?f=6*) that should help. Need to learn extrusion for 3D text effects. This was very easy in Xara 3d & Xara 5 but is not part of Xaralx. 3D seems more difficult in Inkscape but, as I said, learning new software can be a real headache. :frown:

---

