---
title: "Adding the &quot;Retro&quot; theme to Mythbuntu 9.1"
date: 2009-11-08
forum: Mythbuntu
---

### Post by geolizardo on 2009-11-08
I have recently installed Mythbuntu 9.1 and am somewhat disappointed in the lack of themes for non-widescreen TV's.  So I DL'd the [Retro]("http://www.aldorf.no/mythtv/") theme that I had used on my old system.  I put it into the "Themes" folder in /usr/share/mythtv/themes. But I cannot select it as a theme option in the display settings.  I see that this has changed somewhat with 9.1 over 8.04.  Can anyone shed some light on how I can add a theme?

---

### Post by xinix on 2009-11-08
Mythtv 0.22 can not use themes from previous versions.  The retro themes would need to be updated so that it can be used properly in the new version of Mythtv.

---

### Post by Spookster on 2009-11-20
Gah, I've just hit upon the same problem. Quite annoyed, now my entire family has to get used to a new interface. 

The supplied themes are (at best) ugly and (at worst) unusable.

Would love to get Retro working again, but don't really know where to start. Do you know if it's still under active development?

---

### Post by azmyth on 2009-11-20
I think someone is porting the theme over.

[http://www.westnet.com/~chris/Mythtv/Retro-wide.tar.gz](http://www.westnet.com/~chris/Mythtv/Retro-wide.tar.gz)

---

### Post by alexmc on 2009-11-21
I've got a very similar problem. Upgraded my Ubuntu box to Karmic Koala (Ubuntu 9.10) and the front end doesn't have the theme I was using before.

No problem thinks I... I'll just use one of the new themes similar to what I used.

Unfortunately I can't find one which actually displays the file size. This is important for me as several recordings end up as zero bytes long.


I'll be following this thread and see if I can do anything to help...

---

### Post by t3chn0b0y on 2009-11-22
I experienced the same thing switching over.. I am of yet to get
my hands on a widescreen display. But right now my financial situation is stopping me from embarking on a quest for a new one. One thing that bugs though is how it wiped out my custom themes also.. I had a christmas one I created last year, and it was gone after the update.. It was a nice green,red etc.. like christmas lights... :( I guess I will have to figure out the new way of creating one since it is that season again :) :popcorn:

---

### Post by tgm4883 on 2009-11-22
@all
If you had 0.21 themes and they aren't in 0.22, you need to contact the author of those themes and get them to update their theme to work with the new MythUI. 

@Spookster
Ugly is in the eye of the beholder, after all, they can't all be hello kitty themes. And which themes are unusable?

@t3chn0b0y
What do you mean it wiped out your custom themes? Are they just not showing up, or something else?

---

### Post by Spookster on 2009-11-23
> **tgm4883 said:**
> @Spookster
Ugly is in the eye of the beholder, after all, they can't all be hello kitty themes. And which themes are unusable?

OK, now that I've calmed down I apologise for this sweeping statement. I was really just thinking of the new horizontal-scrolling themes, which seem to me to be a step backwards from a usability perspective (you can only see about 5 items at once, and the menus are harder to use). They look great though.

Also, the font sizes on the programme lists seem to have got smaller, and messing with the settings doesn't *seem* to be fixing them. As I don't have a big TV this also annoyed me. Don't know if this is theme-related as such or a general change brought about by the new MythUI stuff.

(I hadn't realised about the lack of backwards compatibility in themes from 0.22 to 0.21. I'm guessing this probably also explains the inexplicable changes to the behaviour of the right / left buttons on the view recordings screen?)

---

### Post by Spookster on 2009-11-23
> **azmyth said:**
> I think someone is porting the theme over.

[http://www.westnet.com/~chris/Mythtv/Retro-wide.tar.gz](http://www.westnet.com/~chris/Mythtv/Retro-wide.tar.gz)

That's great, I'll take a look at that!

---

### Post by tgm4883 on 2009-11-23
> **Spookster said:**
> OK, now that I've calmed down I apologise for this sweeping statement. I was really just thinking of the new horizontal-scrolling themes, which seem to me to be a step backwards from a usability perspective (you can only see about 5 items at once, and the menus are harder to use). They look great though.

Also, the font sizes on the programme lists seem to have got smaller, and messing with the settings doesn't *seem* to be fixing them. As I don't have a big TV this also annoyed me. Don't know if this is theme-related as such or a general change brought about by the new MythUI stuff.

(I hadn't realised about the lack of backwards compatibility in themes from 0.22 to 0.21. I'm guessing this probably also explains the inexplicable changes to the behaviour of the right / left buttons on the view recordings screen?)

To access extra information on the view recordings screen, you can hit I or M, depending on what you want to do.

---

### Post by azmyth on 2009-11-23
> Also, the font sizes on the programme lists seem to have got smaller, and messing with the settings doesn't *seem* to be fixing them. As I don't have a big TV this also annoyed me. Don't know if this is theme-related as such or a general change brought about by the new MythUI stuff.
I think sometimes themers end up hardcoding in the font size so changing the settings don't effect the actual font display.

---

### Post by Spookster on 2009-11-25
> **tgm4883 said:**
> To access extra information on the view recordings screen, you can hit I or M, depending on what you want to do.

Thanks, that's helpful. I don't like having to move from the cursor keys on my remote but it doesn't look like there's any way to restore the old right-arrow functionality. Ah well.

This upgrade of MythTV seems to have brought few improvements and many unwanted changes, at least from my personal perspective.
</whine>

---

### Post by tgm4883 on 2009-11-26
> **Spookster said:**
> Thanks, that's helpful. I don't like having to move from the cursor keys on my remote but it doesn't look like there's any way to restore the old right-arrow functionality. Ah well.

This upgrade of MythTV seems to have brought few improvements and many unwanted changes, at least from my personal perspective.
</whine>

You are welcome to write a patch that will make that configurable and submit it upstream. Besides the right arrow functionality I havent heard much else that people dont like

---

### Post by SiHa on 2009-11-27
> **tgm4883 said:**
> Besides the right arrow functionality I havent heard much else that people dont like
That's about the size of it. And even that I got used to after about a week.

---

