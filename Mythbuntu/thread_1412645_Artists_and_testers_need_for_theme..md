---
title: "Artists and testers need for theme."
date: 2010-02-21
forum: Mythbuntu
---

### Post by xinix on 2010-02-21
I've done some work on creating a new theme.  I'm planning on doing another round of work on it soon and would like to get some feedback.  I already have a list of things to fix/adjust but I'm sure there are other items that need to be added.
One of the major things I want to do is re-make the 'watermark' images.  At the moment I'm using modded images from the Retro and Pear-ody themes; I'd like to use original art when I make the theme available to everyone.

Send me a PM if you are interested in trying the theme and giving me feedback, or if you are an artist willing to help create new art for the project.

Thanks

Edit:
Here are the download links for the theme.  I'll keep these updated as I build the debs.

[COLOR="Red"]UPDATED 5/17/10[/COLOR]

Since 0.23 is now the current stable release, I am no longer maintaining an 0.22 version of this theme.  If you have already been using the 0.23 version please make note of the following.  
After installing this updated version you will need to re-select the theme in the appearance settings.  This is because I have dropped the '0.23' suffix in the theme name.

0.23 Compatible version: [0.4.8]("http://ppa.launchpad.net/6c-theme/ppa/ubuntu/pool/main/m/mythtv-theme-algae/mythtv-theme-algae_0.4.8_all.deb")

More Screenshots
[http://picasaweb.google.com/102884186572787687304/AlageMythtvTheme?feat=directlink](http://picasaweb.google.com/102884186572787687304/AlageMythtvTheme?feat=directlink)

---

### Post by williammanda on 2010-02-21
I can't test it but the theme looks good. I would like to try it out when you are finished.

---

### Post by xinix on 2010-02-27
Wow no responses?  I still need to hammer out some of the layout stuff but I'll go ahead and make this available for people to try.  I'd really like to know what does and doesn't work for you.

Edit:
I've moved the links to the the first post.

---

### Post by kja999 on 2010-02-27
Hi Xinix,

I have had a quick play with it. It all looks nice, and nothing broke whilst using it.
3 things I found might need some work; on the recordings list, you may as well make it full screen as otherwise all the real estate is wasted; in the EPG (from the menu not live tv), the transparency makes it almost unusable in the lower half of the screen; and last, can you add mythmusic ;)

I still prefer a theme which uses normal left/right for navigation, pressing ESC still annoys but seems to be the norm in 0.22, so maybe I need to learn to live with it.

Good work so far though!

---

### Post by geekyhawkes on 2010-02-27
Looks really nice to me, keep up the good work!

---

### Post by xinix on 2010-02-27
> **kja999 said:**
> ... and nothing broke whilst using it.
Glad it worked for you.  It does for me too on my dedicated mythbox, but when I try it on my lappy it's not so good. But then other themes don't play nice on the lappy either.
>  on the recordings list, you may as well make it full screen as otherwise all the real estate is wasted; My intention was to not clutter the fan art.  Most fan art uses the upper half of the image for the important stuff like faces.  A variation that uses the full screen wouldn't be difficult though.  The menu itself only has one item less than the default Mythbuntu theme.
> 
in the EPG (from the menu not live tv), the transparency makes it almost unusable in the lower half of the screen;
I'm trying to figure out what is happening here.  I don't have this problem if I scale the GUI to to fit on my screen without any over-scan; but it does happen if I don't do this.  Thanks for confirming that it's a theme issue and not a quirk in my system.
>  and last, can you add mythmusic ;)
Yes, I don't use mythmusic myself but I can install the plugin and make something for it.

---

### Post by azmyth on 2010-02-27
I'm compiling trunk and I just did a force-depends to install. The images don't show up and the highlight makes the print disappear when scrolling in the horizontal menus. Will the theme work with trunk?

---

### Post by xinix on 2010-02-27
Apparently it doesn't work with 0.23, just 0.22, I just tried it myself.  So something has changed.  I'll have to look into what it is.  Sorry about that.

---

### Post by xinix on 2010-02-27
Ok, I've learned what has changed.  I'll make an 0.23 compatible package.  This also explains why my lappy was unhappy with some themes.

---

### Post by azmyth on 2010-02-28
No worries. I wanted to see if you could provide a tar or src of the theme for those of us who compile since force-depends gives broken packages.

Sorry I didn't send you a PM saying I'd test as I meant to and just forgot as I appreciate people's efforts.

---

### Post by xinix on 2010-02-28
> **azmyth said:**
> No worries. I wanted to see if you could provide a tar or src of the theme for those of us who compile since force-depends gives broken packages.


I'll figure out a place to put a .gz of just the theme.  It's too big to attach to a forum post. 
The reason it breaks for 0.23(trunk) is because there has been a change in the terms that need to be used in a theme's xml file.  So, 0.22 (release) looks for <state name="selected"> but 0.23 (trunk) looks for <state name="selected[COLOR="Red"]active[/COLOR]">.  So the code itself needs to be changed. 
I'm making a few more adjustments, I think I've fixed the EPG problem.  I'll upload a version for 0.22 and one for 0.23 that doesn't require the mythtv-common package.

---

### Post by xinix on 2010-02-28
Ok I've created a version that is compatible with 0.23 and I think I have fixed the EPG transparency issue.  I think the transparency problem may happen with other screens so I need to go back and check them all.

---

### Post by xinix on 2010-03-07
The transparency issue should be fixed on all the screens now.  I'll get back to fixing/improving the layout.

The links are updated in the original post.

---

### Post by xinix on 2010-03-14
Fixed the "Create DVD" layout.  It should be usable,  at least you can see which recording you have selected.

---

### Post by 4dognight on 2010-03-14
I just tried your new theme, and I like it.
One thing though, I find the text a bit small when Im navigating through my recordings. Maybe the currently highlighted recording, could be enlarged or something to make it more readible. The background picture helps, but some shows dont have them, and even then you still need to try and read which episode it is.
I also downloaded the menu link on the first post, but Im not sure which menu it refers to.

---

### Post by xinix on 2010-03-14
> **4dognight said:**
> I just tried your new theme, and I like it.Thanks
> 
One thing though, I find the text a bit small when Im navigating through my recordings. Maybe the currently highlighted recording, could be enlarged or something to make it more readible. 
 I'll see what I can do to make the font larger.  I'm pretty sure I used the same size font as the default theme.
> 
The background picture helps, but some shows dont have them.  Not all shows have fan art.  At least not all shows have fan art that gets automatically downloaded.  You can add your own if you want.  These images aren't part of the theme; just loading them.
> 
I also downloaded the menu link on the first post, but Im not sure which menu it refers to.
You select this menu in the same window where you selected the new theme.  It's on the fist page under "Menu Theme" It's called 6C-Menu.  I need to rename it to match the UI theme name.

---

### Post by 4dognight on 2010-03-15
OK, I got your menu to load. 
Do you know of an easy way to get fanart for TV shows that dont have them? I was thinking of taking a still from one of the shows, but not sure how to go about doing it.
In the FE config , I see a screenshot path. But was unable to figure out how to make it work.

---

### Post by xinix on 2010-03-16
> **4dognight said:**
> OK,
Do you know of an easy way to get fanart for TV shows that dont have them? I was thinking of taking a still from one of the shows, but not sure how to go about doing it.

You can look online for fan art if you want.  I've gotten some from [http://thetvdb.com](http://thetvdb.com) when the script didn't find anything.  To manually grab a screenshot I'll (not often) use 'scrot' (it's in the repo).  Basically I pause the show on the frame I want to use for fan art, clear the OSD, and via ssh I run this command.```
DISPLAY=:0.0 scrot
```  The non ssh way I've done this is to CTRL+F1 then run this command```
sleep 10 && DISPLAY=:0.0 scrot
``` and before the 10 seconds rundown CTRL+F7

Once you have your image put it in the directory you set for fan art.  The file should be named exactly what myth calls the show including spaces and '_fanart' before the sufix, eg. Name of Show_fanart.png

---

### Post by 4dognight on 2010-03-16
I got screenshots to work. Someone else posted same question.
[http://ubuntuforums.org/showthread.php?t=1430119](http://ubuntuforums.org/showthread.php?t=1430119)

I am able to fill in my missing fanart now. Having trouble with 20/20 though, as the '/' is confusing it.

On another note, When the FE starts I get an error.

WARNING: The theme (6C-Menu) is missing a themeinfo.xml file, ignoring.

Any update on making the highlighted show easier to read? I was thinking maybe if it was enlarged like the main menu text does. Maybe not that big though.

---

### Post by xinix on 2010-03-17
> **4dognight said:**
> I got screenshots to work. Someone else posted same question.
[http://ubuntuforums.org/showthread.php?t=1430119](http://ubuntuforums.org/showthread.php?t=1430119)

I am able to fill in my missing fanart now. Having trouble with 20/20 though, as the '/' is confusing it.

Glad you found a solution.  I bet there is some way around the '/' issue but I'm not savvy enough to know how.

> 
Any update on making the highlighted show easier to read? I was thinking maybe if it was enlarged like the main menu text does. Maybe not that big though.
    At the moment I haven't done much in this area. Most of my effort has been on the DVD burning screens.  I did look and noticed that the episode name was one size smaller than the show name; so I made it the same size.  
    If I make the font much larger I have to create more space between the selections and this would result in even fewer choices being available.  Things look funny if I leave the spacing the same but make the selected font larger.  The selected font gets cut off by the other titles.

---

### Post by 4dognight on 2010-03-17
The background picture usually will let you know what TV series it is, just by looking at it. So making the text larger for the episode is more important. Also, you have the TV series name included with the episode, as well its on the left hand pane. So it is actually duplicated. You could drop the TV series name and just have the episode info on the right pane. That would give you more room for a larger font for the episode info.

---

### Post by xinix on 2010-03-17
> **4dognight said:**
>  Also, you have the TV series name included with the episode, as well its on the left hand pane. So it is actually duplicated. You could drop the TV series name and just have the episode info on the right pane. That would give you more room for a larger font for the episode info.
The list of series names on the left helps you filter episodes to a specific series. The list on the right shows your recordings in the order that they recorded; if you remove the show name from that list you end up with a list of episode names but no show title for them.  So you need the series name in both lists.  The problem with larger fonts is only partially a horizontal issue. The main thing is the vertical space it requires.  If I make it any bigger there would be fewer shows in the list.

---

### Post by xinix on 2010-03-22
> **kja999 said:**
> ...and last, can you add mythmusic ;)
!
I've started doing this.  The main player and mini-player are nearly complete.  I need to adjust the layout a bit, but I probably won't make any big changes unless inspiration hits hard (or I get a really good suggestion).  I might actually start using MythMusic more often now.  I still need to do more with the playlist editing scree.

Changes:
Cleared out extra files, re-structured file layout,  continued to work on improving theme layout.  Improvements to:  Music (including miniplayer), Gallery, Video screens.

As always, updated links are in the 1st post.

---

### Post by kja999 on 2010-03-22
MythMusic is looking good! Thanks for the addition ...

---

### Post by uncle hammy on 2010-03-22
I think the theme looks great!  One thing I'd mention, is none of the menus (i.e. Pressing 'm' button in the view viedos screen) are done, so the default back to the preivous theme.

---

### Post by xinix on 2010-03-22
> **uncle hammy said:**
> I think the theme looks great!  One thing I'd mention, is none of the menus (i.e. Pressing 'm' button in the view viedos screen) are done, so the default back to the preivous theme.

The menu should be different than the default Mythbuntu theme.  You are correct that there are similarities.  The biggest change is that the whole screen should darken when you bring up the menu.  The default is to draw a black box around the buttons.  

Let me know which you are getting.  If it's not working for you then there is something that needs to be fixed.  I can attach screenshots to see a side by side comparison if you want.

---

### Post by uncle hammy on 2010-03-22
That's what I'm getting.  I guess just because of how similar they are, and somehow in my head they don't seem to "match" the theme itself, I thought they weren't done.  Apologies.

---

### Post by xinix on 2010-03-22
Hey no apology needed.  I agree they don't match the theme.  I will be working on buttons that will match the theme better.  I've put these off so that I can match them to the theme and not the theme to the buttons.

---

### Post by uncle hammy on 2010-03-23
My other critique would be the guide.  

I have my short date format set to "Tue 3/23" because I really like to see the day when I'm going forward in the guide (in fact, truth be told, the day is more important to me than the date itself).  Because of the limited space for the date in the top left portion, it shows up as "T.." for me.

I'm also a little on the fence of having so many of the titles have the second line cut off for the sake of displaying so many channels on the screen at once.

Just my 2 cents.

---

### Post by xinix on 2010-03-23
> **uncle hammy said:**
> I have my short date format set to "Tue 3/23" 

Where do you set this option?  I tried finding it but I didn't see it right away in general of program guide settings.

---

### Post by uncle hammy on 2010-03-24
> **xinix said:**
> Where do you set this option?  I tried finding it but I didn't see it right away in general of program guide settings.
Utilities/Setup>Setup>Appearance>Page 4

---

### Post by xinix on 2010-03-24
Ha! I should have looked there.  I'll see how much space the longer format needs.

---

### Post by uncle hammy on 2010-03-25
My wife also complained last night that the time isn't displayed anywhere.  I didn't actually notice myself, but never under estimated the power of the waf. :)

---

### Post by xinix on 2010-03-28
Created new buttons, changed gallery view for MythVideo,  adjusted EPG screen.

---

### Post by uncle hammy on 2010-03-28
Seriously looks awesome.  Thanks for the time too....told my wife she's married to a big player, and I got the time put in for her :).  

I did notice that Watch Recordings>M>Change Group Filter the menu still has the old buttons.

The only thing left that I've seen, is in Videos.  I think fan art for the background in Browse mode (my personal preference) would be nicer than the standard background.

---

### Post by xinix on 2010-04-04
Minor layout adjustments.  Switched watermarks to a base and emblem method.  This change helped reduce the final package size.

Moving forward,  I'm reaching a point where I'll focus on the 0.23 compatible version.  This version of MythTV supports a few features in themes that the 0.22 version does not.  Most importantly I should be able to set gradient fills in shapes instead of using images with gradients as overlays to achieve the same effect.

As usual updated links are in the first post, thanks for the feedback!

---

### Post by uncle hammy on 2010-04-13
I have just noticed an issue with the guide from Live TV (the one with the video preview).  The rows for the channel names have more height than the rows for the guide data.  This makes the data not line up with the channel the data belongs to rather quickly.  See the attached image.  8-1 belongs to Ellen, 8-2 belongs to Law and Order and so on.  Who Wants to be a Millionaire belongs to 13-1, even though 13-1 lines up with Target Weather Network....King of the Hill belongs to channel 17-1 which isn't even displayed on the screen.

---

### Post by xinix on 2010-04-14
Ok, I've fixed the channel list issue in the live TV program guide.  I also changed the layout to be more consistent with the non video version.

I changed the watch recordings screen.  The font for the selected recording should be bigger.  I learned how to make this bigger without it overlapping with the titles above and below it.

MythNetVision is themed, but I think I need to continue to work on it some more.

Updated links on in the first post.

---

### Post by uncle hammy on 2010-04-15
The new watch recordings screen is really crowded, especially on the actual program (far right side) with the new, hd, ect details.  In fact, the HD, New, etc actually end up overlapping the program below it.  This is hard to look at (see the second, blown up image).  FWIW, my resolution is 1280 x 720.

With the larger fonts, the rest of the sections just seem really lopsided IMHO, because the spacing crowds the item below, and leaves plenty of space to the item above.

P.S.  My wife watches Ellen, not me :)

---

### Post by xinix on 2010-04-15
Yikes! thats not good or right.  I think it's a 0.22 vs 0.23 thing.  I've been using 0.23 for a while.  I'll fix the 0.22 compatible theme shortly.

I've attached a shot of how it should look.

Edit I've removed the screenshot and updates the one in the OP.

---

### Post by uncle hammy on 2010-04-15
That looks great!  It veru well could be a 0.22 vs 0.23 thing.  I have been holding off until 10.04 to go to 0.23.  Though I suppose it is probbaly pretty safe to upgrade at this point anyways.

---

### Post by xinix on 2010-04-15
Fixed the watch recordings issue in 0.22.

---

### Post by uncle hammy on 2010-04-15
The highlighted item is completely blanked out in the new version.  In the image, I have Ellen selected (the blank space in the middle) and there are actually 3 episodes, and I have the middle one selected.

---

### Post by xinix on 2010-04-15
> **uncle hammy said:**
> The highlighted item is completely blanked out in the new version.  In the image, I have Ellen selected (the blank space in the middle) and there are actually 3 episodes, and I have the middle one selected.

Yeah, that was the original thing that tipped me off about needing to create themes for both versions of myth.  It's such a simple  fix yet such a hassle if it isn't.  All should be fixed now.

---

### Post by JellyBellean on 2010-04-16
I have noticed that all of your artwork (and the XML many of your screens seem to be based on) is taken directly from pre-existing themes.  I was wondering why you don't provide any attribution for the work of others?  Also, are you sure that all of that artwork you borrowed is available under the GPL?  For any artwork which isn't GPL, have you contacted the author for permission to share it under that license?

---

### Post by uncle hammy on 2010-04-16
It is no longer blank.  It is back to the old style, it is simply highlighted.  No larger font, no HD, New, etc details.

---

### Post by xinix on 2010-04-16
> **JellyBellean said:**
> I have noticed that all of your artwork (and the XML many of your screens seem to be based on) is taken directly from pre-existing themes.  I was wondering why you don't provide any attribution for the work of others?  Also, are you sure that all of that artwork you borrowed is available under the GPL?  For any artwork which isn't GPL, have you contacted the author for permission to share it under that license?

If you read the OP I mention that the art is from other themes, That would be why I asked for others to help create new ones, but yes the are GPL and the final properly released version will link to their source and attribute to them.  Which art work are you questioning?

The XML is mostly based on the 'default-wide' or the default Mythbuntu theme.  Remember that the Mythbuntu theme was for a very long time a mod of the ProjectGreyhem theme. You make it sound like I simply crammed a bunch of files into a folder and crossed my fingers.

---

### Post by JellyBellean on 2010-04-16
> **xinix said:**
> If you read the OP I mention that the art is from other themes, That would be why I asked for others to help create new ones, but yes the are GPL and the final properly released version will link to their source and attribute to them.  Which art work are you questioning?

The XML is mostly based on the 'default-wide' or the default Mythbuntu theme.  Remember that the Mythbuntu theme was for a very long time a mod of the ProjectGreyhem theme. You make it sound like I simply crammed a bunch of files into a folder and crossed my fingers.

It wouldn't be that hard to provide some sort of attribution now, though, would it?  A readme file and some accounting of where all the artwork came from in the post where users can download your packages?  I see artwork from the Mythbuntu theme, from the "demo" theme, and several others.  The layout and artwork of all of your buttonlist selectors is a direct lift from the XBMC mediastream theme (probably taken from the MythUI demo theme).  I've also noticed you've added artwork taken from the Arclight theme recently, so it seems like you are moving towards using more artwork made by others rather than less of it.  Not that there's anything explicitly wrong with taking your artwork from elsewhere, it just seems like it would be courteous to acknowledge that many/most of the visual elements in the theme weren't created by you.  I am pretty sure Arclight and Mythbuntu are GPL, but I don't think there's any explicit license on the demo theme that you seem to have incorporated parts of, nor do I know for sure about mediastream.  Your menu icons, what's the source there?  Are the icons themselves GPL, or are they creative commons?  If creative commons attributable, you're already in violation.  Just some things to think about.

When you make attributions, hopefully you can confirm the licenses of the original works?

---

### Post by xinix on 2010-04-16
Working on a readme right now. I'm also disabling the links and what not until everything is clean.

Yes the selectbar is a mod from the MythUI demo and I need to confirm the use of the image or eliminate it all together.  The button layout is not. It's pretty much the default layout moved to the bottom and stretched out. Not an uncommon arrangement.

The watermarks (menu icons) are from the [Retro theme]("http://www.aldorf.no/mythtv/")

Pear-ody theme, here's a link to the [source for the images]("http://www.thisclicks.com/assets/mythTV/"), [and this about their use]("http://ubuntuforums.org/showpost.php?p=7383224&postcount=9")

and the current default Mythbuntu and old default mythbuntu theme, which was a mod of the ProjectGrayhem theme.

The audio/video prop icons have been replaced by simple text entries instead,  this was a change I was going to include in the next update since an image of text can really just be text.

---

### Post by jbman on 2010-04-16
Keep up the good work on your theme.

I like how its the best bits from whats around at the moment as I am not 100% happy with anything right now.

---

### Post by JellyBellean on 2010-04-16
> **xinix said:**
> Working on a readme right now. I'm also disabling the links and what not until everything is clean.

Yes the selectbar is a mod from the MythUI demo and I need to confirm the use of the image or eliminate it all together.  The button layout is not. It's pretty much the default layout moved to the bottom and stretched out. Not an uncommon arrangement.

The watermarks (menu icons) are from the [Retro theme]("http://www.aldorf.no/mythtv/")

Pear-ody theme, here's a link to the [source for the images]("http://www.thisclicks.com/assets/mythTV/"), [and this about their use]("http://ubuntuforums.org/showpost.php?p=7383224&postcount=9")

and the current default Mythbuntu and old default mythbuntu theme, which was a mod of the ProjectGrayhem theme.

The audio/video prop icons have been replaced by simple text entries instead,  this was a change I was going to include in the next update since an image of text can really just be text.

Thanks a lot for this info-- I know that any lack of attriburtion wasn't a malicious or intentional thing, it's just one of those things people can get touchy about and I didn't want to see any problems arise (and better to resolve any minor issues sooner than later).

Great work on the theme, can't wait to see how it pans out.

---

### Post by rich mason on 2010-05-12
Really nice, more subtle than some themes and shows lots of info in the program guide - like it a lot. I think it has a lot of potential. Would not be surprised to see it included some day.

---

### Post by xinix on 2010-05-17
> **rich mason said:**
> ...subtle...

I like that description.

I've dropped the 0.22 compatible versions since the current stable version is 0.23.  I also updated the 0.23 version so that the name no longer has the version number in it, this means you'll have to reselect the theme in the appearance settings.

And yes the selectbar is a new image.

---

### Post by pankaj5k on 2010-05-18
I love this theme. I too hope that it is included in the official release. I just have a minor quibble with the transition from UI to playback in the recordings and video screens. Is it be possible to replace 'Dont panic' and 'Video dialog loading' message with the spinner animation ?

Thanks and best regards, 
   Pankaj

---

### Post by geekyhawkes on 2010-05-29
Great theme, looks really nice on my newly upgraded 10.04 machine!  One thing that i would like to see is a slightly more refined mythmusic screen.  Is there any chance that this could be looked at again when you get chance?

Thanks, keep up the good work!

---

### Post by JEStone on 2010-06-05
Awesome. now my default theme.

thanks

---

### Post by geekyhawkes on 2010-06-06
Also my default theme now, ace with JAMU and the fanart.  One question on the DVD screen (mythvideo), I have fanart and cover art yet when i select a film from gallery view i just have a large ? displayed.  What metadata do i need to populate this?

---

### Post by xinix on 2010-06-08
> **geekyhawkes said:**
> Also my default theme now, ace with JAMU and the fanart.  One question on the DVD screen (mythvideo), I have fanart and cover art yet when i select a film from gallery view i just have a large ? displayed.  What metadata do i need to populate this?

There's nothing you need to do.  It's something I need to fix on my end.  I'll update later in the evening.

What changes would you make to Mythmusic?  I really have done minimal work on this part of the theme because it still uses the old UI structure which isn't quite as nice.

---

### Post by tnat on 2010-06-09
I love this theme. Thank you for working on this!!!

---

### Post by tnat on 2010-06-10
Is there a possibility to get a similar looking OSD-theme?

:roll:

---

### Post by geekyhawkes on 2010-06-11
Thanks for the reply, mythmusic wise, its difficult to suggest really as you said, the orignal UI is a bit weak.  I quite like your current layout but think it would be better if you were to add a visualiser window somewhere (for albumart to be displayed during playback).  

I also think you have scope to reduce the size of the playlist window (so it maybe only takes up half of the height of the screen), which might buy you more screen real estate to play with.  Awesome theme so far, keep up the great work!

---

