---
title: "mythtv 0.23 Arclight theme background"
date: 2010-04-17
forum: Mythbuntu
---

### Post by Eldis on 2010-04-17
Whats up with Arclight themes background images?

tendrils1 - 3.png are 1920x1080 resolution images that look like someone stretched a thumbnail.

Awesome theme but that background just can't be, it has to be a mistake.

To show what I mean:

This is what I would imagine the background to look like more or less:
[http://www.fecitfacta.com/Arclight/Gallery.html#12](http://www.fecitfacta.com/Arclight/Gallery.html#12)

This is what the background image is:
[http://svn.mythtv.org/trac/browser/trunk/myththemes/Arclight/Backgrounds/tendrils1.png](http://svn.mythtv.org/trac/browser/trunk/myththemes/Arclight/Backgrounds/tendrils1.png)

---

### Post by tgm4883 on 2010-04-17
I'm not sure I understand what you mean. I haven't seen that in the theme itself. Can you take a screenshot of what you are seeing?

---

### Post by Eldis on 2010-04-17
Sorry took me a second was missing, gnome-screenshot it was in gnome-utils package incase someone is wondering.

Anyway the screenshot:
[[IMG]http://i4.aijaa.com/t/00677/6080831.t.png[/IMG]](http://www.aijaa.com/v.php?i=6080831.png)

As you can see it does not look right.

---

### Post by Flecko on 2010-04-17
Just installed the 10.04 beta and noticed this as well. Ugly, ugly, ugly...can anything be done to fix it?

---

### Post by Eldis on 2010-04-17
Well yes, we can do something to fix it but I think it's not supposed to be that way.

Goto the theme folder in my case it's:
/usr/share/mythtv/themes/Arclight/Backgrounds

you will find 3 images there tendrils1-3.png move those somewhere and put some other image there pref something high ress like 1920x1080 a photo or maybe a gnome/xfce/kde desktop background. Then edit in the Arcligth folder the file qtlook.txt

edit the line:
```
str BackgroundPixmap=Backgrounds/<someimageofyourchoosing>.png
```

restart frontend, but like I said there has to be mistake, I hope atleast.

---

### Post by theRealGBee on 2010-04-17
It's not a mistake. It was the background the themer chose. He likes it, that's **all** that matters.

---

### Post by tgm4883 on 2010-04-17
It's not a mistake. It's a [mosaic effect]("http://www.google.com/search?hl=en&safe=off&q=mosaic+effect&aq=f&aqi=g10&aql=&oq=&gs_rfai=").

---

### Post by Eldis on 2010-04-18
> **theRealGBee said:**
> It's not a mistake. It was the background the themer chose. He likes it, that's **all** that matters.

Are you sure he chose that on purpose and it's not a mistake and he just hasn't noticed ?

In any case I've changed the bg on mine and thanks to the theme creator for a nice theme, but if he happens to read this thread I would like to him to reconsider the bg images.

---

### Post by iamlindoro on 2010-04-18
> **Eldis said:**
> Are you sure he chose that on purpose and it's not a mistake and he just hasn't noticed ?

I'm sure.

---

### Post by Flecko on 2010-04-18
None of the screenshots on the arclight website have that background...its hideous. I'm going to change it locally...but I think it should be changed for everyone. I actually thought it was a mistake when I first saw it.

In fact, I bet the community would vote to have it changed. Just my opinion...but I can't be the only one...

---

### Post by theRealGBee on 2010-04-18
News flash - You don't get a vote.

Open source does NOT mean that the community gets to decide how things are done, it just means you are free to change it. How about writing your own theme, then we can all tell you it looks hideous.

---

### Post by Eldis on 2010-04-18
Very well it's working as intended then. Still a great theme just not too happy to have to tweak it.

And I doubt anyone will say the theme itself is ugly just the background. Anyway just wanted to ask what I've now found out. If the dev of the theme reads this take it as feedback the rest of the theme is great.

---

### Post by tgm4883 on 2010-04-18
> **Eldis said:**
> Very well it's working as intended then. Still a great theme just not too happy to have to tweak it.

And I doubt anyone will say the theme itself is ugly just the background. Anyway just wanted to ask what I've now found out. If the dev of the theme reads this take it as feedback the rest of the theme is great.


Ok, I've installed Arclight to see what this was all about. I see the background in question and I like it. As said before, the author of the theme likes the background and that is all that matters. There will be no vote on it as on this topic your opinion simply doesn't matter. 

If you don't like it, there are other themes you can choose to run. [http://www.mythtv.org/wiki/Theme](http://www.mythtv.org/wiki/Theme)

If you don't like any of those themes. You can even make your own. [http://www.mythtv.org/wiki/MythUI_Theme_Development](http://www.mythtv.org/wiki/MythUI_Theme_Development)  I won't hold my breath to see this though, as people like yourself seem to think they are entitled to certain things and expect to get whatever they want. After all, that is why you are still complaining about a background that someone volunteered their time (ie. Not paid) to create isn't it?

---

### Post by Eldis on 2010-04-18
> **tgm4883 said:**
> 
If you don't like any of those themes. You can even make your own. [http://www.mythtv.org/wiki/MythUI_Theme_Development](http://www.mythtv.org/wiki/MythUI_Theme_Development)  I won't hold my breath to see this though, as people like yourself seem to think they are entitled to certain things and expect to get whatever they want. After all, that is why you are still complaining about a background that someone volunteered their time (ie. Not paid) to create isn't it?

I didn't expect a change if it really was what the dev intended, I just doubted that it was. But you are right I doubt I will make a mythtv theme, but maybe I'll end up making bigger changes to the existing if the licences allow it.

Still I think everyone needs some feedback, both good and bad and mine was mainly positive. I've been writing software for over 10 years and without feedback I wouldn't have improved as much as I have.

---

### Post by Flecko on 2010-04-18
My apologies if my comment about "hideous" offended anyone. It came off sounding much harsher than intended.

As for my vote comment...I know that there aren't votes on topics like this. It was just meant as a figure of speech.

If the is the way it is intended, then  there is nothing more to say. Thanks for setting me straight.

---

### Post by Lepy on 2010-04-19
The default background is pretty neat imo, but adding some pictures from interfacelift to the backgrounds folder really helps spice things with this new theme and really helps mythtv look amazing for once!

On the same note, does anyone know how to add custom watermarks? I've been looking at the arclights xml files but can't figure out how to reference custom watermarks I've made to custom entries in ~/.mythtv/mainmenu.xml

---

### Post by Lepy on 2010-04-22
Silly me, adding watermarks to MythUI works just as it did in .22 with any other theme. I thought arclight might do it different.

I created some custom launcher icons, what do you think: [http://i43.tinypic.com/5noqph.jpg](http://i43.tinypic.com/5noqph.jpg)

The icon dimensions are 759x245, like the standard watermarks, but  as you can see, the blue selection overlay bleeds a little on the right-hand side of the image. This is not a deal breaker but does anyone know a remedy for this?

---

### Post by davecurtains on 2010-04-23
Nice icons for xbmc and boxee - fancy sharing your updates?

Cheers.

---

### Post by Lepy on 2010-04-26
Yeah, I can upload them tomorrow.

In the meantime, here is a better shot of the transparency, another xbmc icon, and proper button location (no overlay bleed):

[http://i44.tinypic.com/aads0k.jpg](http://i44.tinypic.com/aads0k.jpg)

---

### Post by Lepy on 2010-05-03
I've been sick, but I finally got around to uploading the icons.

[IMG]http://i42.tinypic.com/wvqz4g.jpg[/IMG]
[IMG]http://i39.tinypic.com/axxvrn.jpg[/IMG]
[IMG]http://i43.tinypic.com/ztt21k.jpg[/IMG]
[IMG]http://i42.tinypic.com/2ep4nxy.jpg[/IMG]

Copy /usr/share/mythtv/themes/defaultmenu/mainmenu.xml to /home/yourusername/.mythtv/mainmenu.xml and add your entry as usual:
```
   <button>
     <type>MENU_XBMC</type>
     <text>XBMC</text>
        <description>Browse Movies, TV, and Music</description>
     <action>EXEC /usr/bin/xbmc</action>
   </button>

   <button>
     <type>MENU_BOXEE</type>
     <text>Boxee</text>
        <description>Watch Internet TV</description>
     <action>EXEC /opt/boxee/run-boxee-desktop</action>
   </button>

    <button>
        <type>MENU_HULU</type>
        <text>Hulu</text>
        <description>Access Hulu Content</description>
        <action>EXEC /usr/bin/huludesktop %F</action>
    </button>

```

Additions under <buttonlist name="menu"> to /usr/share/mythtv/themes/Arclight/menu-ui.xml (area is crucial or the selection overlay will bleed):
```
                         <state name="MENU_BOXEE">
                                <imagetype name="watermark">
                                <area>0,0,765,245</area>
                                <filename>/path/to/boxee.png</filename>
                                </imagetype>
                        </state>
                        <state name="MENU_XBMC">
                                <imagetype name="watermark">
                                <area>0,0,765,245</area>
                                <filename>/path/to/xbmc.png</filename>
                                </imagetype>
                        </state>
                        <state name="MENU_HULU">
                                <imagetype name="watermark">
                                <area>0,0,765,245</area>
                                <filename>/home/to/hulu.png</filename>
                                </imagetype>
                        </state>

```

Copying menu-ui.xml to your ~/.mythtv folder does not seem to work. Also, to keep things organized, I have created a watermarks folder with a path like this: /home/username/.mythtv/watermarks/boxee.png

---

### Post by davecurtains on 2010-05-08
> **Lepy said:**
> I've been sick, but I finally got around to uploading the icons.


Cheers for sharing these dude.  Just added them to my system and they really do clean it all up and look nice.

Now to find a nice background somewhere ;-)

Cheers,

---

### Post by nickrout on 2010-05-08
Just to be clear here the pixellated backgrounds are what the author intended. The screenshots on the net are with fanart included for various shows.

See this thread [http://www.gossamer-threads.com/lists/mythtv/users/434755#434755](http://www.gossamer-threads.com/lists/mythtv/users/434755#434755)

Thanks to Lepy for his icons. I spent a while yesterday trying to figure out how to do the transparency in gimp and gave up!

---

### Post by Lepy on 2010-05-08
[QUOTE=davecurtains]Cheers for sharing these dude. Just added them to my system and they really do clean it all up and look nice.

Now to find a nice background somewhere 

Cheers,[/QUOTE]No problem! Hope you enjoy them. I was getting fed up with seeing so many popcorn/ticket icons on my main menu!

 The tendrils backgrounds are really cool, but I prefer to find my own. Any 720 or 1080 picture will work fine dumped into /usr/share/mythtv/themes/Arclight/Backgrounds (or, I guess, a symlinked Backgrounds folder) with the added benefit of the background being randomized on re-load or menu change. 

I personally love the photography found on interfacelift, so I've been dumping random 1080 images from there. This works fine for my purposes. As I do use myth as my main frontend, I don't use jamu, opting to trans-code recordings to mkv and cheat on myth with xbmc for any recordings I want to archive!

[QUOTE=nickrout]Thanks to Lepy for his icons. I spent a while yesterday trying to figure out how to do the transparency in gimp and gave up!
[/QUOTE]

nick, the easiest way to apply transparency in gimp (off the top of my head) is 1.) flatten your image 2.) right click on the newly created background layer and select "Add Layer Mask" -> "White (full opacity) 3.) select the gradient tool and start opacifying away!

I'm not sure how to emulate the exact opacity level found in the author's original icons (I assume he used a macro), so I did all of these by eye. If someone knows a way to get the exact gradient to match the original icons, I'll gladly re-upload some new icons.

---

### Post by Chewiesw on 2010-05-11
Love the new theme, I would however like to tweak the video plot font size a little. It is a little small on my setup and I am wondering how i can increase it? I have tried increasing the font sizes in myth setup but nothing sems to have changed.

---

### Post by nickrout on 2010-05-11
I suggest you join the mythtv-theming mailing list.

---

### Post by mala88 on 2010-05-13
Thanks for the tip. I also thought there was a problem with the theme when I saw the blue background. 

Is there a way to prevent the theme configuration from being overwritten during each update?

---

### Post by ilium007 on 2010-05-25
I would LOOOVE my MythTV to look like this !!!

[http://www.fecitfacta.com/Arclight/Gallery.html#13](http://www.fecitfacta.com/Arclight/Gallery.html#13)

Awesome stuff !

---

### Post by Lepy on 2010-05-25
> **ilium007 said:**
> I would LOOOVE my MythTV to look like this !!!

[http://www.fecitfacta.com/Arclight/Gallery.html#13](http://www.fecitfacta.com/Arclight/Gallery.html#13)

Awesome stuff !

If you are already using Arclight or newer theme, I believe jamu will help you gather metadata and attain your perfect mythtv setup.

---

### Post by ilium007 on 2010-05-26
It was not the metadata I was after, it is that nice horizontal menu and cool backgrounds !!

---

### Post by nickrout on 2010-05-26
> **ilium007 said:**
> It was not the metadata I was after, it is that nice horizontal menu and cool backgrounds !!

The author gave up the horizontal menu after people didn't like it. I agree with them, but it's a matter of taste, not correctness.

The backgrounds in the screenshots are from the metadata (which includes fanart). So to get that look, yes you need the metadata.

---

### Post by LowSky on 2010-06-11
I hate the pixelated look so I changed mine to this image, it looks so much better, and isn't hurting my eyes.

---

### Post by ilium007 on 2010-06-12
Do you know where we can get a HD version of this image ? 1920 x 1080 would be great.

---

### Post by chibiace on 2010-06-15
heh i thought this was a glitched image resize thing. good to know its easy to swap out, its a very nice looking theme

---

