---
title: "mencoder as backend in DeVeDe: resulting DVD video playback stutters"
date: 2012-05-07
forum: Multimedia Software
---

### Post by veroslav on 2012-05-07
Hi,

I posted in another thread about issues I am having with DeVeDe and the black menus it produces when using ffmpeg as the backend. That thread can be found here:

[http://ubuntuforums.org/showthread.php?p=11913300&posted=1#post11913300](http://ubuntuforums.org/showthread.php?p=11913300&posted=1#post11913300)

In this thread I would like to get help with the issue I am having when using mencoder as the backend when producing a DVD in DeVeDe application.

The resulting DVD is fine with respect to the menus, but the playback stutters quite significantly throughout. It makes the viewing and enjoying the video impossible. The audio playback is fine.

I am running Ubuntu 12.04 (64-bit), stock installation of everything, DeVeDe version is 3.21.0. I am creating a menu with custom menu background, custom menu sound and a single DVD title from a VOB.

I have tried the above on both my laptop and my desktop computer and I have the same problem on both. :(

Could anyone help me track down this issue? I will gladly provide more details if needed.

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by jromer on 2012-05-07
I'm having same issue when using devede 3.21 on Ubuntu 12.04. 

Using FFMPEG files encodes properly but menu is not created correctly. 

If I use mencoder option I get the menu but then the video stutters. 

Both outputs unplayable...

---

### Post by jromer on 2012-05-07
I did find a solution to get DeVeDe to work...however this solution uses the FFMPEG option rather than the mencoder...

[http://ubuntuforums.org/showthread.php?t=1971910](http://ubuntuforums.org/showthread.php?t=1971910)

---

### Post by veroslav on 2012-05-08
Hi jromer,

thank you for your replies. It's nice to hear that I am not alone with this issue, even though I am naturally sorry to hear that you are also experiencing the same problem.

Have you tried updating the ffmpeg from the ppa suggested in this thread:
[http://ubuntuforums.org/showthread.php?t=1971910](http://ubuntuforums.org/showthread.php?t=1971910)

What was the outcome? Visible menu, no stutter?

Also, it looks as though there is some progress on DeVeDe, which might solve the issues we are having, have a look here:

[http://groups.google.com/group/devede-forum/browse_thread/thread/2db1628bde35d590#](http://groups.google.com/group/devede-forum/browse_thread/thread/2db1628bde35d590#)

Regards,
Veroslav

---

### Post by jromer on 2012-05-08
Yes, I did install the PPA for FFMPEG and now I'm getting the menu and the video is encoding correctly...So it's working now! Thanks

However, like you I still have the stuttering problem when using mencoder as the back-end...


AND after reading your initial post I see that I inadvertly changed the subject. I appoligise for that.

---

