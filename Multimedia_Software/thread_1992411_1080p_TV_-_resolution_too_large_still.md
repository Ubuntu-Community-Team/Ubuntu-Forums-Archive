---
title: "1080p TV - resolution too large still"
date: 2012-05-31
forum: Multimedia Software
---

### Post by derekcentrico on 2012-05-31
I have a 1080P TV that I use for a Media Center.  I'm new to Ubuntu for media needs coming from Windows 7.  On Windows 7 I had to use the NVidia application to come up with a custom resolution for the TV so that the entire screen would fit.

On Ubuntu, the top menu bar and system tray is entirely outside the viewing area.  The Ubuntu application bar on the left side of the screen is only about 1/3 visible.

What would be the best way to determine and set the appropriate screen resolution?

---

### Post by papibe on 2012-05-31
Hi derekcentrico.

That may be another problem: [Overscan]("http://en.wikipedia.org/wiki/Overscan")

If so, you have 2 options to solve it:

First (recommended): Some TV's have the ability to set how the signal is reproduced. In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Play with the options available on your TV, may be the option is not easy to see. Check your manual or research about it on the Internet.

Second: the 'Nvidia X Server Settings' has an option to correct overscan manually. Check [this]("http://www.ypass.net/blog/2010/04/nvidia-overscan-correction-fixed-in-latest-drivers/") article, or [this]("http://smartsoftwarefactory.blogspot.com/2011/01/correct-tv-overscan-using-ubuntu-nvidia.html") other one.

Tell us how it goes,
Regards.

---

### Post by shz1 on 2012-05-31
Depending on the tv you have, there are options in your tv menus to correct this. I had the same issues and my Samsung has some auto feature that finds the correct resolution to make the screen fit.

---

### Post by derekcentrico on 2012-05-31
Thanks to the both of you for the answers.

It seems that switching from Natural to Native on this old Toshiba LCD works for fitting Ubuntu properly.

Now, I must readjust my Revue and PS3 resolutions accordingly.

I thought it unfortunate that Nvidia no longer appears to have an over-scanning option in the Ubuntu configuration app.  Or, it wasn't available to me for some reason.

---

