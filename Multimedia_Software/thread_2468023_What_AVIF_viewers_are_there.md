---
title: "What AVIF viewers are there?"
date: 2021-10-16
forum: Multimedia Software
---

### Post by Paddy Landau on 2021-10-16
**EDIT:** See [post #14]("https://ubuntuforums.org/showthread.php?t=2468023&p=14063623&viewfull=1#post14063623") for details of the bug reports.

For those who don't know, [AVIF is the upcoming]("https://avif.io/") new image and video format, so efficient that Netflix uses it on supported devices.

But.

Ubuntu seems to have a major problem supporting AVIF.

The newest version of GIMP on Flatpak (but not Snap, for some reason) supports AVIF.

But I want an image viewer that supports AVIF! I have tried so many different viewers without success.

According to [Ubuntu Handbook]("https://ubuntuhandbook.org/index.php/2021/08/gthumb-3-11-4-avif-heif-support/") and [OMG Ubuntu]("https://www.omgubuntu.co.uk/2021/09/thumb-3-12-avif-heif-image-support"), gThumb version 3.11.4 and higher supports AVIF. Well, I've installed gThumb 3.12 (from Flatpak), and it doesn't.

Am I perhaps missing a library? What can I do to get an AVIF viewer?

Thanks

---

### Post by Dennis N on 2021-10-16
Are you sure about gthumb?
I downloaded a test image, and opened in gthumb (see cropped screenshot). The metadata shows it's HEIF/AVIF image. 
Yet, the gthumb version is:
```
[dmn@Sydney ~]$ gthumb --version
gthumb 3.10.4, Copyright © 2001-2010 Free Software Foundation, Inc.

```
So I'm a bit confused, as the article indeed says gthumb 3.12 added this support. Maybe because this gthumb is provided by Manjaro and they have included the support, while that's not true of Ubuntu's package?

ADDED:
Using new Ubuntu 21.10, I tested the Flatpak gthumb, 3.12, and can confirm it will not display the image. Maybe a later update it will.

---

### Post by Paddy Landau on 2021-10-16
Thanks for the reply, Dennis.

I see that Manjaro supports it, but not Ubuntu. So, that means that something is missing from Ubuntu &#8212; and from the Flatpak installation, because Flatpak is supposed to contain all of the dependencies.

I'll see if I can figure out how to get hold of whoever creates the Flatpak, and ask about it.

---

### Post by Paddy Landau on 2021-10-16
Quick question, Dennis:

If you go to gThumb > Preferences > Saving, what do you see under Default options?

I see JPEG, PNG, TGA, TIFF, WebP (screenshot below).

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289287&stc=1[/IMG]

---

### Post by Paddy Landau on 2021-10-16
I've [reported the issue]("https://gitlab.gnome.org/GNOME/gthumb/-/issues/200") with gThumb. If you agree, please log in there and press the thumbs-up to vote for it. Thank you

In the meantime, I'm still open to suggestions for an alternative viewer that supports AVIF!

---

### Post by Dennis N on 2021-10-16
> If you go to gThumb > Preferences > Saving, what do you see under Default options?
The image options for saving in Manjaro's gthumb are the same as you show. To test, I tried "save as" with the image used in post #2, and this only works if I choose one of the supported save formats (such as png). So this version of gthumb can view these AVIF images, but not save them in that format.

---

### Post by Paddy Landau on 2021-10-16
Thanks, Dennis. Well, I'll have to see what the gThumb team tells me, or wait for a recommendation for an alternative AVIF viewer.

---

### Post by Dennis N on 2021-10-16
What about the PPA that's mentioned in the OMG article? Did you try that?

---

### Post by Paddy Landau on 2021-10-16
> **Dennis N said:**
> What about the PPA that's mentioned in the OMG article? Did you try that?
I didn't because the installation of the PPA gave an error.

However, I've just retried, and it worked!

Thank you. I'll mark this as solved.

EDIT: Just updating with that PPA, not bothering to install anything new, fixed AVIF for existing apps such as Image Viewer and Nautilus.

---

### Post by monkeybrain20122 on 2021-10-17
> **Paddy Landau said:**
> 

The newest version of GIMP on Flatpak (but not Snap, for some reason) supports AVIF.


It depends on the libheif version against which gimp is linked. It doesn't work if libheif is < 1.9.  I compiled gimp on Ubuntu 20.04, libheif in repo is 1.7 so it didn't work, upgrading libheif to 1.20 from ppa and recompile gimp (2.10.28 though it is supposed to work since 2.10.22) and it works.

---

### Post by Paddy Landau on 2021-10-17
> **monkeybrain20122 said:**
> It depends on the libheif version against which gimp is linked. It doesn't work if libheif is < 1.9.  I compiled gimp on Ubuntu 20.04, libheif in repo is 1.7 so it didn't work, upgrading libheif to 1.20 from ppa and recompile gimp (2.10.28 though it is supposed to work since 2.10.22) and it works.
Thanks for this. I'll stick to Flatpak, because it has version 2.10.28, whereas the standard repository has only 2.10.18. I'm not going to compile the stuff myself — it's too complicated for me :)

---

### Post by monkeybrain20122 on 2021-10-18
And this [https://github.com/novomesk/qt-avif-image-plugin](https://github.com/novomesk/qt-avif-image-plugin)

I tested in on Ubuntu 20.04 with nomacs, it works (nomacs is a qt app from the repo, not kde dependencies)

---

### Post by Paddy Landau on 2021-10-19
> **monkeybrain20122 said:**
> And this [https://github.com/novomesk/qt-avif-image-plugin](https://github.com/novomesk/qt-avif-image-plugin)
I tested in on Ubuntu 20.04 with nomacs, it works (nomacs is a qt app from the repo, not kde dependencies)
Thanks. I've got it working with the other PPA.

I think that I should raise this as a bug, to encourage AVIF support to be built into the next LTS (22.04).

---

### Post by Paddy Landau on 2021-10-19
I see that this has already been raised in a bug report.

If you agree, please upvote it (go to the bug report, log in if required, and select the green text near the top left). It would be helpful to also upvote the associated requests.

[LIST]
[*][Bug #1946567]("https://bugs.launchpad.net/pinta/+bug/1946567")
[*][Bug #1917512]("https://bugs.launchpad.net/ubuntu/+source/viewnior/+bug/1917512")
[*][Bug #1917518]("https://bugs.launchpad.net/ubuntu/+source/gwenview/+bug/1917518")
[/LIST]

---

### Post by monkeybrain20122 on 2021-10-19
> **Paddy Landau said:**
> I see that this has already been raised in a bug report.

If you agree, please upvote it (go to the bug report, log in if required, and select the green text near the top left). It would be helpful to also upvote the associated requests.

[LIST]
[*][Bug #1946567]("https://bugs.launchpad.net/pinta/+bug/1946567") 
[*][Bug #1917512]("https://bugs.launchpad.net/ubuntu/+source/viewnior/+bug/1917512") 
[*][Bug #1917518]("https://bugs.launchpad.net/ubuntu/+source/gwenview/+bug/1917518") 
[/LIST]


Done.

---

