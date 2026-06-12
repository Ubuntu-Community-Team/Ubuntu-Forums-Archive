---
title: "Firefox does not scroll when I use mouse wheel and mouse pointer is on flash object"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by andrei.kouznetsov on 2006-11-11
I'm just curious: is it a common problem when Firefox does not scroll when you use mouse wheel and your pointer is above flash object?
In my case it does not scroll. It is not a big problem but it irritates me :(

---

### Post by bruenig on 2006-11-11
Yeah it won't do that. It is not a bug per se, just the reality of flash.

---

### Post by Spin Doctor on 2006-11-20
I must disagree. If it was a just reality of flash, how come flash does not show this behavior when I run it on my XP Pro, and FF 1.5.0.8. Then I can use my mousewheel, to move my page even if I am on a flash element.

I must agree with andrei that this is very irritating, and I am wondering if anyone has a solution to this problem, which does exist and is not just a typical behavior of Flash. 

I upgraded Flash on my Edgy to version 9, to see if problem still exists, and it sure does.

//Spin Doctor

---

### Post by Spin Doctor on 2006-11-21
Andrei,

I guess I found a workaround solution to this problem. There are two extensions to firefox that will make this scrollwheel issue with flash disappear. 

The first one is **Flash Block**. With this extension activated all flash elements will still remain on the page, but they are not loaded in, and you can scroll over them with the mousewheel. If you want to see a specific flash, you have to click on it to activate it, and load it in.

The other extension is **Adblock Plus**. This is the solution I prefer. Just create wildcard filters to block the flashadvertisments on the major sites you visit, and the flash elements will not even load in and occupy space in your browser. Added bonus is that the webpages will load alot quicker.

//Spin Doctor

---

### Post by emrahustun on 2008-01-22
one year and 2 mounts after this topic's last entry, i want to ask if anybody has a solution.

we still can't scroll in firefox when mouse is over a flash object.

suggestions?

---

### Post by Spin Doctor on 2008-01-24
It is so irritating I am considering writing to Adobe for answers....this is a huge usability issue for Linux and Firefox. I think it is funny to run Wine and firefox with flash and see the correct behaviour.

---

### Post by finer recliner on 2008-01-27
i would also like to see a real solution for this annoyance.

anyone? anyone?

---

### Post by Steveway on 2008-01-27
As pointed out before: It is a problem with flash.
Flash for Linux is not the same like Flash for Windows.
You have to ask Adobe to fix this.

---

### Post by javier.ldb on 2008-02-18
Anyone? Is there anybody out there? Years dealing with this sh***t

---

### Post by emrahustun on 2008-02-18
i'm waiting a solution for this issue. it's so irritating.

---

### Post by Spin Doctor on 2008-02-20
I have good news folks! Running Hardy with Firefox 3 beta 3, with flashplayer 9, this issue has been resolved...I can now scroll over any flash element with my mousewheel!! What a great day it is =) =D>

---

### Post by javier.ldb on 2008-02-20
Awesome!

---

### Post by Yuki_Nagato on 2008-02-20
When you scroll with the middle wheel in the Firefox application, you are scrolling through Firefox.  When the pointer hits the Flash Application, the focus changes from the Firefox application to the Flash application.  The function of the mouse wheel suddenly changes.

---

### Post by emrahustun on 2008-02-20
yes. with firefox 3 beta 3 and flashplayer 9, it's working fine.

hobaaa elleri göriyim:mrgreen:

---

### Post by Mad_Gouki on 2008-02-24
Yeah, everyone has this problem.  To the best of my knowledge, it has to do with certain flash components.  MediaPlayback is the one I read the problem exists with, and it does not even have to be used in the video, if it is in the library when the video is compiled it will cause it.
linky:  [http://www.hostingforum.ca/843374-flash-pages-containing-mediaplayback-component-won-t-scroll.html](http://www.hostingforum.ca/843374-flash-pages-containing-mediaplayback-component-won-t-scroll.html)
it would be interesting to see if somebody who knows flash could make a flash file without that component as part of their library and then test to see if it fixes it.
also, i don't know if the gnu flash plugin does it too, but for sure the closed source one does.

The easiest fix for this I can think of is to deny input of the scroll up or down buttons to the flash window.  The same behavior is present, to some extent, in a very long box of code on vbulletin, when the mouse is over the box of code, scrolling down has no effect, only when you have reached the bottom of the box, does the scrolling of the main page continue.  The cursor actually changes the 'focused' object, i guess you could say.  For example, if you had a webpage with 10 of those ugly ancient frames with pages that go longer than the screen can display, and you were to hold the scroll down button, only the frame in which the mouse resided would scroll down.

If there is a way to either deny the input of the scrolling buttons (or any buttons, make it configurable :D ) to the flash video, or if there were a way to force the scrolling when mousing over a flash video to affect the web page, those would be decent fixes.  Both could be done, possibly, in the firefox source, or as an add-on to firefox.  I don't know enough about how the systems work to say whether or not it could be done tho.

---

### Post by Mad_Gouki on 2008-02-24
> **Spin Doctor said:**
> I have good news folks! Running Hardy with Firefox 3 beta 3, with flashplayer 9, this issue has been resolved...I can now scroll over any flash element with my mousewheel!! What a great day it is =) =D>
Thank you good sir, for making my day! :D I am now enjoying firefox3!  I didn't even know it was a public beta.

---

### Post by kennygunie on 2008-04-04
I'm have Hardy x64, FF 3 Beta 4, Flash 9.0 r115, scroll does not work always on flash objet :(

---

