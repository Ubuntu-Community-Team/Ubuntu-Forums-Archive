---
title: "full screen flash svideo outputs image on primary screen, want it on TV screen"
date: 2009-12-11
forum: Multimedia Software
---

### Post by sdowney717 on 2009-12-11
is there a way to put full screen on the svideo out screen when running a browser?
if i open vlc it will stay on the svideo out as full screen

if i use a web browser and click the full screen option, it puts the full screen on the pc monitor not on the tv.

I can run it cloned screens and then of course it works, but i dont want to clone screens since the resolutions differ.

---

### Post by markbuntu on 2009-12-11
Apparently flash full screen defaults to screen position 0,0 which is the upper left corner of your desktop. It has been this way for a long time. You could try putting your tv to the left side of your desktop.

However, I recently got a flash update for my hardy install and now some flash full screen plays on my right screen (hulu, google, some youtube but not all) and some on my left (some youtube) when I have firefox open on the right screen but all play on the left when firefox is there.  It does not do this on Jaunty or Karmic or previously on Hardy, full screen is always on the left. 

It is very strange behavior.

---

### Post by sdowney717 on 2009-12-11
Vista does the same thing I think I remember this.
the point being lets say you want to watch a video on the TV. You cant unless you clone the display.

[http://social.technet.microsoft.com/Forums/en/w7itpromedia/thread/85f37708-d1f6-4329-a40e-e751d70c5e13](http://social.technet.microsoft.com/Forums/en/w7itpromedia/thread/85f37708-d1f6-4329-a40e-e751d70c5e13)
found this about vista full screen on secondary display, there is a workaround 'compatability mode'
but who knows, i dual boot so i can try it out
I will keep looking for something for ubuntu

i use nvidia driver 195.22

another forumite says put it to left so i will try
[http://ubuntuforums.org/showthread.php?t=973631](http://ubuntuforums.org/showthread.php?t=973631)

---

### Post by sdowney717 on 2009-12-11
yes that worked.

screen icons have to be dragged off the tv screen back on the desktop.

at first it gave me a strange error, the desktop was a mess, but I kept rearranging left, right below and it finally worked.

it is not ideal, i cant work on the pc and watch full screen as it pulls away the focus back away from the TV.

in xp, when running an ati card, there was theatre mode where you could do this, i think

---

### Post by sdowney717 on 2009-12-11
any ideas about editing our linux flash binary file like you can for 
windows?

[http://www.youtube.com/watch?v=qwH_-C2-93E](http://www.youtube.com/watch?v=qwH_-C2-93E)

also this site works full screen is centered BUT, youtube the image is down on the right side and cuts off a good part of it.
[http://www.thewb.com/shows/smallville/exile/527b41b47f](http://www.thewb.com/shows/smallville/exile/527b41b47f)

---

### Post by markbuntu on 2009-12-11
I have seen some old bug reports at adobe about this and they used to say that it was not a problem but a security feature but more recently they have changed their stance and it seems this is under review. Maybe that's why I have such wierd behavior with the flash update in Hardy, maybe they are trying some things out. We can only hope.

---

### Post by sdowney717 on 2009-12-11
[http://my.opera.com/d.i.z./blog/2009/04/22/watch-fullscreen-flash-while-working-on-another-screen?startidx=0#comments](http://my.opera.com/d.i.z./blog/2009/04/22/watch-fullscreen-flash-while-working-on-another-screen?startidx=0#comments)

found a patched flash for windows. I think i will try this running firefox in wine with this and see what happens

tried it and cant go full screen with firefox, wine and flash

had to switch it back to right side of screen. all popup windows were going over to tv. I wish adobe would change this behavior.

---

### Post by sdowney717 on 2009-12-14
[http://www.hulu.com/labs/hulu-desktop-linux](http://www.hulu.com/labs/hulu-desktop-linux)
nice working app for ubuntu. I am running it on karmic

hulu desktop full screens on the TV fine.

I also found out if there is a popout button on a flash page you can full screen it to the TV and it will stay there using the maximize page button in the corner

---

