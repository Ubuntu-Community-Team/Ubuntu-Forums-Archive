---
title: "Firefox 3 and browsing QTVR..."
date: 2008-05-12
forum: Multimedia Software
---

### Post by Ron F. on 2008-05-12
I am running Ubuntu 8.04 / Firefox 3. I want to view QTVR images (virtual reality panoramas) available online. The standard plugins available in the repositories work fine for Quicktime video, (.mov extension,) but they do not work for QTVR files, (unfortunately also using the .mov extension.)

Something like the freepv plugin might work, but then I lose the ability to view Quicktime video - hardly a solution.

My solution has been to install the window's version of Firefox and Quicktime 7.4.5 (without iTunes) under wine, and then I can view QTVR. That works.

Is there a way to use Apple's Quicktime plugin under wine, but call it from the Linux version of Firefox 3? Then I would not need to switch between different versions of the browser for different kinds of content!

-Ron

---

### Post by celem on 2009-05-12
I think that your lack of response is telling. I just finished an extensive search and tried some java programs that were supposed to work, but the bottom line answer is NO, there is currently no way to view QTVR on linux.

If anyone out there wants to prove me wrong and direct us to a solution, I'd love to try it.

---

### Post by leonox on 2009-06-23
Actually there is FreePV since 2006, I have worked on the project and I'm working at the moment in bringing QTVR to the VLC media player... FreePV stills have some limitations and you will not be able to display all the panoramas that exist out there...

Other problem that you will face, is that the plug-ins for video and the FreePV's plug-in share the mime type for mov files... thus I'm working in adding QTVR support to VLC.

:popcorn:

---

### Post by PGScooter on 2009-06-25
Is this why I can't watch the quick tour here:
[http://www.apple.com/mobileme/features/gallery.html](http://www.apple.com/mobileme/features/gallery.html)
?

Or is there something I can install?

---

### Post by celem on 2009-06-25
Ron F.,
That isn't the issue. It is NOT QTVR When I click on the link in Firefox on XP, the video plays. When I click on the link in Firefox on Ubuntu Linux, only an invitation to download QuickTime is presented. However, if you look at the source, you'll see that the video URL is embedded in the page, identified as class="movieLink"at URL:
[http://movies.apple.com/media/us/mac/mobileme/2009/tours/apple-mobileme-mobileme_gallery-us-20090212_r640-10cie.mov](http://movies.apple.com/media/us/mac/mobileme/2009/tours/apple-mobileme-mobileme_gallery-us-20090212_r640-10cie.mov)

If you paste this into the Firefox address bar, it plays on my Ubuntu 9.04. Thus the problem is not the .mov file but rather how this bit of HTML code is being processed. I'm no html guru so I don't understand how the URL is triggered in this page.

---

### Post by PGScooter on 2009-06-27
celem, thanks for the tip, that works decently well. It looks like its a firefox problem, as you say. If its not fixed in the upcoming 3.5 version, I will post a bug report. Sorry ron f. to have hijacked this thread a little

---

### Post by Rallg on 2009-10-07
Since we're getting close to the 9.10 release: I haven't been able to get FreePV to function on 9.10 beta. The svn 166 download (Oct 8 2009) compiled and installed OK. But when I call the program, it fails. Terminal tells me:

freepv-glut: error while loading shared libraries: libfreepv.so.0.0: cannot open shared object file: No such file or directory

But the library is in fact present, in /usr/local/lib

UPDATE: I made links to libfreepv.so and libfreepv.so.0.0 and put the links in /usr/lib. Then, freepv launches.

---

