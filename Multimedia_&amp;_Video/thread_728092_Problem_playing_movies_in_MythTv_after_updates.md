---
title: "Problem playing movies in MythTv after updates"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by anigodin on 2008-03-18
Hello all,

I built a Mythbuntu station a few months ago and I'm still learning how everything works.

A couple of weeks ago there was a hugh bundle of updates ready to be installed, a big part of them regarded the MythTV itself. I installed all the updated and when I opened the frondend again I saw it's skin changed to a grayish skin (no, that's not my problem).
Yesterday I tried to watch a movie in the frontend and someting strange happened:
I entered the multimedia section from the main screen, moved to the 'Video' section and pressed enter and nothing happened.. I cant go inside. 
I thought maybe something was changed in the configuration of the video location, so I tried to enter the video setup section and got the same result - nothing.

Does anybody came across a problem like this? how do I solve it? by the way, the video can be played outside the myth system so the problem must be there..

Many thanks.

---

### Post by agamotto on 2008-03-18
I also have had the same thing happen.  I also seem to have lost the Internet Streams, but at least it gives me an error code about different versions of mythlib... 

I will let you know if I discover anything!

---

### Post by anigodin on 2008-03-18
Problem Solved... Thanks to the help of my personal Linux Guru :-)

It seems that the updates were also an UPGRADE of the intire mythTV system.
In the new version, the mythvideo and the mythdvd are united and in order to be able to watch videos in the frontend you need to do as follows:

enter synaptyc and search for 'myth'

in the last 10 results you'll find mythvideo which is installed but will be marked with a small star. when you right-click on it you'll see the option 'mark for upgrade' - choose it and confirm the next window that will tell you that mythdvd will be removed.

apply the changes

exit synaptic and enter myth frontend - the video library is now accessible.

---

