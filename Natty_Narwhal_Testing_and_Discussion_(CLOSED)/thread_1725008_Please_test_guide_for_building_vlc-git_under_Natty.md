---
title: "Please test guide for building vlc-git under Natty"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by andrew.46 on 2011-04-09
I have recently updated a guide for building the development version of vlc under Ubuntu to now cater for Natty Narwhal:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

With Natty being released soon can I ask a few brave Natty users to test this guide out? I have tested it under 64bit Natty and it works well enough but I am always keen to hear from other users, other systems, other points of view...

Thanks,

Andrew

---

### Post by MadCow108 on 2011-04-09
this is wrong:
if [ "$(uname -m)" = "x86_64" ]; then
  echo 'This section is for 32bit installations only!!'
else

---

### Post by andrew.46 on 2011-04-09
> **MadCow108 said:**
> this is wrong:
if [ "$(uname -m)" = "x86_64" ]; then
  echo 'This section is for 32bit installations only!!'
else

This is intended to stop 64bit users installing codecs that only work with the vlc *--enable-loader* compile option under a 32bit installation. What appears wrong with it?

---

### Post by mc4man on 2011-04-09
andrew - you're pretty much good to go, built, ran fine on 32 bit
The loader seems to be a bit limited to current value, video wise will work on the rare occasion it's desired, wmal is a bit hit or more likely  miss w/ 1.2+
(the snapshot option isn't needed anymore

Couldn't resist pausing after bootstrap and adding back apple trailers  - still works fine. (don't use imdb
For natty don't like global menus in vlc so edited vlc's .desktop Exec= to 
```
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 vlc %U
```
can be done before (in vlc/share) or after install

---

### Post by MadCow108 on 2011-04-09
> **andrew.46 said:**
> This is intended to stop 64bit users installing codecs that only work with the vlc *--enable-loader* compile option under a 32bit installation. What appears wrong with it?

yes you are right.

for some reason I read it was for 64 bit installations and the logic is wrong way round ...

---

### Post by andrew.46 on 2011-04-09
> **mc4man said:**
> andrew - you're pretty much good to go, built, ran fine on 32 bit

Thanks again for looking at this, a few problems here with Natty Beta on VirtualBox, I suspect the VB people are waiting for Natty release before they commit themselves...

> (the snapshot option isn't needed anymore

Indeed it appears to have been removed a little over a week ago:

[http://git.videolan.org/?p=vlc.git;a=commit;h=382b435433fe62fc58b25ad9600be64c3d6d5d3f](http://git.videolan.org/?p=vlc.git;a=commit;h=382b435433fe62fc58b25ad9600be64c3d6d5d3f)

and so I have removed the option; not quite sure what he means by "*We have better ways to take snapshots nowadays.*"

> Couldn't resist pausing after bootstrap and adding back apple trailers  - still works fine. 

It would be tempting to add the apple lines back in, should not take much with sed, and of course you have pointed out the [change in the code]("http://git.videolan.org/?p=vlc.git;a=commitdiff;h=377ea4956ae17cdab28720be492cfbf436676fb8;hp=cb98df1ce4b368f94254508c135b66a59d68e1b5") before :).

---

### Post by andrew.46 on 2011-04-09
> **MadCow108 said:**
> yes you are right.

for some reason I read it was for 64 bit installations and the logic is wrong way round ...

No, thank you for looking at this :). When Natty is released and I have it running well in VirtualBox (as opposed to the slightly dodgy performance at the moment!) I aim to tidy up these *if* conditions a little...

---

### Post by nokangaroo on 2011-04-14
Works perfectly well, even though I had not deleted vlc-1.1.8 previously (because I was testing the script).
Vertical refresh still does not work with the nvidia driver, but this is a nvidia issue, not a vlc issue. vlc -git works perfectly with ubuntu lucid and nvidia-current, so for people who want to use vlc with the nvidia driver I recommend using lucid.

Maybe the script should delete the remaining vlc-1.1.8 files automatically since they are not needed.

---

### Post by nokangaroo on 2011-04-14
P.S. When I tried to update vlc on Maverick I got an error message from the update script that I had made changes to my repository without committing them (even though I had run the script before, and it worked). As I am not a vlc developer and had no idea what the script was talking about (I am not aware of having made any changes, but I browsed the files which must have changed some access times), I simply deleted vlc_build and started from scratch, which is kind of overkill. Maybe the update script should ignore changes made by the user and simply update the repository, since developers are unlikely to use this script.

That way, I could also copy the vlc_build directory over from backup or another install, thereby saving myself and the vlc people some bandwidth.

---

### Post by mc4man on 2011-04-14
> **nokangaroo said:**
> Works perfectly well, even though I had not deleted vlc-1.1.8 previously (because I was testing the script).
Vertical refresh still does not work with the nvidia driver, but this is a nvidia issue, not a vlc issue. vlc -git works perfectly with ubuntu lucid and nvidia-current, so for people who want to use vlc with the nvidia driver I recommend using lucid.

Maybe the script should delete the remaining vlc-1.1.8 files automatically since they are not needed.

I see no tearing w/ more modern hardware, though w/ an older AGP card the 2.XX.. drivers did introduce _the possibility_ of tearing in _some_ vids (the best driver I found for AGP cards was the 185-195 drivers which are not available post lucid

As far as removing a packaged vlc prior to building if installed that would be up to Andrew, it's a good thing to do though I guess if building a vlc there would be some presumption of awareness of this.

(removing just the vlc-data package will remove all other vlc packages

---

### Post by andrew.46 on 2011-04-17
> **nokangaroo said:**
> Maybe the script should delete the remaining vlc-1.1.8 files automatically since they are not needed.

Good point, I shall include a short note at the beginning of the guide. Can I say that I am quite heartened to see that nobody has found any show-stopping problems :).

---

### Post by andrew.46 on 2011-04-26
All seems to be working well with a daily build from yesterday so I will mark this thread as solved, before the whole section is shutdown, and thanks to all who had a look :). Big screenshot of the successful build [here....]("http://www.andrews-corner.org/images/vlc_natty.png")

---

