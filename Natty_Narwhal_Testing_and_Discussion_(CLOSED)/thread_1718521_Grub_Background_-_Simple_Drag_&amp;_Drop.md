---
title: "Grub Background - Simple Drag &amp; Drop"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by drs305 on 2011-03-31
Copy a .jpg, .png or .tga image to /boot/grub, update Grub and you now have a Grub menu background. If you haven't previously set up an image or theme, it can be that simple! The rest is, if you pardon the pun, just background info.

Note: If the image name includes spaces, the image is copied to a (hidden) file named  *.background_cache.** and an "unexpected operator"  message is generated while running 'update-grub'. The image will still appear during boot, with Grub2 using the file */boot/grub/.background_cache.**. Thanks to forum member *Anduu* for posting this behavior.

I haven't spent much time with Grub 1.99RC as improvements continue and I didn't want to post anything until Natty was officially released. But this was so easy I thought I'd pass it on. 

Besides the simplicity of activating a background, Grub 2 now should auto-detect the resolutions and provide what it considers the best resolution, and it will stretch any image to fill the screen. So it's pretty easy to add a bit of eye candy.

**Procedure:**
1. Copy any image (jpg, png or tga) to the /boot/grub folder.
2. Run "sudo update-grub".
3. Done.

**Disclaimer:**
I've had problems with Natty in VirtualBox, and I'm not having consistent success with the background image in a VM. If it doesn't work in a VM, don't spend a lot of time trying to fix it.

**Background & Additional Info:**

Image Priority:
[LIST=1]
[*]"GRUB_BACKGROUND=" setting in /etc/default/grub
[*]First image found in /boot/grub
[LIST]
[*]The first image found, in this order:  jpg, JPG, jpeg, JPEG, png, PNG, tga, TGA
[*]If multiple images of the same extension, alphanumerically.
[/LIST]
[*]Wallpaper designated in /usr/share/desktop-base/grub_backgorund.sh (if desktop-base installed)
[*]/usr/share/images/desktop-base/desktop-grub.png (if desktop-base is installed)
[*]Default theme (no image): Aubergine background, selected item black on light gray background)
[/LIST]

**Gotchas**
[LIST]
[*]Don't forget to run  "sudo update-grub"
[*]If you have multiple distros on your system, remember the change must be made to the controlling Grub
[*]Grub 1.99 RC  or later.
[*]Images should be RGB, i.e. non-indexed (in GIMP, Image > Mode) and jpeg images should be 8-bit.
[/LIST]

Note: For a brief explanation of font color selection, see Post #4.

Attached are two simple background images:

---

### Post by Rubi1200 on 2011-03-31
Thanks for posting this excellent information. I haven't tried this yet, but will be sure to let you know if it works as soon as the opportunity arises.

---

### Post by ranch hand on 2011-03-31
A timely post for me.  Thank you very much.

Have not been able to set an image on my Debian Testing install.  Just not working at all.

Read this.  Checked /etc/default/grub.  No GRUB_BACKGROUND= in there.  Put it in there along with a .png image.  Ran update-grub and the bugger found the image.

Have to reboot and see what I need to do to the font colors.

Thanks a bunch.

---

### Post by drs305 on 2011-03-31
> **ranch hand said:**
> 
Have to reboot and see what I need to do to the font colors.

I knew the issue of font colors would come up eventually ...  ;-)

When the user specifies a custom background, the Grub devs decided to be conservative and specified a black/white font scheme. They were kind enough to comment on it in Step 7 of /etc/grub.d/05_debian_theme but left it to the user to figure out how to deal with the font colors when using custom backgrounds.

Whether you use the GRUB_BACKGROUND setting in /etc/default/grub or just stick an image in /boot/grub, here is a way to designate the colors.

First, keep in mind that Grub 2 considers *black* used as the second color entry as *transparent*. You will see the background image wherever *black* is the second entry (e.g. green/black = green text on transparent background).

To change the font colors, edit /etc/grub.d/05_debian_theme, around line 98:
```
gksu gedit +98 /etc/grub.d/05_debian_theme
```
Add lines 2 & 3, using the colors you desire.
> 
	echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
[COLOR="DarkRed"]echo "  set color_normal=light-gray/black"
echo "  set color_highlight=green/black"
[/COLOR]	if [ -n "${2}" ]; then

In this example, the highlighted line has a green font on a transparent background (i.e. there is no highlighted bar). The unselected text is light gray. If you want the highlighted text to have a colored bar across the screen, use a color other than ../black.

Save the file, then update Grub.
```
sudo update-grub
```

---

### Post by Quackers on 2011-03-31
Thanks for the info :-)
I couldn't figure how to change the font colour from the (now) standard white text, so I just used a dark coloured background :-)

---

### Post by ronacc on 2011-03-31
thanks for the info .

---

### Post by ranch hand on 2011-03-31
> **drs305 said:**
> I knew the issue of font colors would come up eventually ...  ;-)

When the user specifies a custom background, the Grub devs decided to be conservative and specified a black/white font scheme. They were kind enough to comment on it in Step 7 of /etc/grub.d/05_debian_theme but left it to the user to figure out how to deal with the font colors when using custom backgrounds.

Whether you use the GRUB_BACKGROUND setting in /etc/default/grub or just stick an image in /boot/grub, here is a way to designate the colors.

First, keep in mind that Grub 2 considers *black* used as the second color entry as *transparent*. You will see the background image wherever *black* is the second entry (e.g. green/black = green text on transparent background).

To change the font colors, edit /etc/grub.d/05_debian_theme, around line 98:
```
gksu gedit +98 /etc/grub.d/05_debian_theme
```Add lines 2 & 3, using the colors you desire.

In this example, the highlighted line has a green font on a transparent background (i.e. there is no highlighted bar). The unselected text is light gray. If you want the highlighted text to have a colored bar across the screen, use a color other than ../black.

Save the file, then update Grub.
```
sudo update-grub
```
Yup, that is how you do it.   I have to see what it looks like before messing with it though.

I can't just reboot anytime I may fell like it.  One of the work units that I get through boinc does not have many check points and they are BIG slow buggers.  Even with the "keep apps in memory" checked you still can loose hours of work.  I manage the buggers so that I can have times when none of them are running.  The rest of the work units I get are no problem.  You may loose a minute or two at the most.

Got to go. I see that the WU I was waiting on finished up 3 minutes ago.

---

### Post by drs305 on 2011-03-31
> **ranch hand said:**
> Got to go. I see that the WU I was waiting on finished up 3 minutes ago.

And besides, it's time to get the herd back up to pasture.

---

### Post by Quackers on 2011-03-31
drs305, is it just me, or has your name disappeared (from near your Ubuntu Master Roaster title)?

---

### Post by ronacc on 2011-03-31
what colors are valid ?

---

### Post by drs305 on 2011-03-31
> **ronacc said:**
> what colors are valid ?

I made a color chart in the community doc here. I expect these to still be correct. Scroll down a bit from where this link takes you in the page:
[https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming]("https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming")

black, blue, brown, cyan, dark-gray, green, light-cyan, light-blue, light-green, light-gray, light-magenta, light-red, magenta. red, white, yellow

---

### Post by ronacc on 2011-03-31
thanks .

---

### Post by ranch hand on 2011-03-31
> **ronacc said:**
> thanks .
Those are not the only colors you can use.  They are the only ones that are recognized as words.  you can use numeric color code to designate any color or shade you want.

I admit to being too lazy for that.  Did it once and it does work.  I have to look up the code and it just is not worth, it for me, to spend the time for something that is on the screen as long as the menu is.

---

### Post by nm_geo on 2011-03-31
> **Quackers said:**
> drs305, is it just me, or has your name disappeared (from near your Ubuntu Master Roaster title)?
Not just you Quackers.
Good question have you got an answer?

---

### Post by drs305 on 2011-03-31
> **nm_geo said:**
> Not just you Quackers.
Good question have you got an answer?

He has, but I'm not telling what I told him. Hint: It's not your machine...

:-\"

---

### Post by nm_geo on 2011-03-31
> **drs305 said:**
> He has, but I'm not telling what I told him. Hint: It's not your machine...

:-\"
Yeah i kinda figured that.  No problem I also noticed cariboo's were missing from earlier threads too. Just wondering and i love puzzles. Thus linux LOL

---

### Post by ronacc on 2011-03-31
> **ranch hand said:**
> Those are not the only colors you can use.  They are the only ones that are recognized as words.  you can use numeric color code to designate any color or shade you want.

I admit to being too lazy for that.  Did it once and it does work.  I have to look up the code and it just is not worth, it for me, to spend the time for something that is on the screen as long as the menu is.

theres an easier way to get the color values , just open gimp click on the foreground color  and when the selector comes up just pick your color and the #'s will be shown ( see SS )

---

### Post by karmila on 2011-03-31
> **ronacc said:**
> theres an easier way to get the color values , just open gimp click on the foreground color  and when the selector comes up just pick your color and the #'s will be shown ( see SS )

I would prefer use gcolor2 for this purpose ;)

---

### Post by ranch hand on 2011-04-01
> **ronacc said:**
> theres an easier way to get the color values , just open gimp click on the foreground color  and when the selector comes up just pick your color and the #'s will be shown ( see SS )
I am simple.  Of coarse that would be the easy way to do it.  Also see the color on the image that you are using.

Give me another brain and you could probably call me a half wit.

Thanks.

---

### Post by drs305 on 2011-04-01
One other matter related to font colors that I'll record here, since I'll probably make up a unified thread elsewhere when the Natty testing forum is closed down.

I've already detailed the extra steps you must take if you use a custom background: To change the font & background colors insert or modify lines in /etc/grub.d/05_debian_theme (see Post #4).

**[COLOR="DarkRed"]Real-Time Testing[/COLOR][COLOR="Navy"] Graphics[/COLOR] & [COLOR="Purple"]Font Colors[/COLOR] at the Grub2 menu**

Font & background changes take effect immediately when editing the Grub2 menu from the grub prompt, so immediate feedback while testing color combinations is possible.

[LIST=1]
[*]At the Grub2 menu (hold SHIFT during boot if it doesn't display. But hey, if it doesn't display why are you wasting time with a grub background ;-) ).

[*]Press 'c' to get the grub prompt.


[LIST]
[*]**Change the background image:**
[LIST]
[*]```
background_image <path/filename>
```
[*]Example: background_image /boot/grub/natty.png  # Assumes prefix is set to (hdX,Y)/boot/grub
[/LIST]


[*]**Change the font & background colors:**
[LIST]
[*]```
set <selection>=color1/color2
```
[*]Example: set menu_color_highlight=yellow/blue
[/LIST]
[/LIST]


[*]To see all current settings type *set* at the grub prompt.
[*]Changes to *color_normal* are seen immediately at the grub prompt. To see the menu changes press ESC to return to the Grub2 menu.
[/LIST]

**[COLOR="DarkRed"]color1/color2[/COLOR]**

Two colors must be designated when assigning colors; I'll use the *color1/color2* convention.
[LIST]
[*]*color1* is the text color


[*]*color2* is the background color or transparency (black)
[LIST]
[*]*color2* must be 'black' for a background image to be visible. 
[*]'black' as *color2* is regarded as transparent.
[*]Any other color will hide all or part of any background image being used. 
[/LIST]
[/LIST]

**[COLOR="DarkRed"]Menu Settings[/COLOR]**
[LIST]
[*]**Selected Entry within the Grub Menu Border (one line):**
[LIST]
[*]```
menu_color_highlight=color1/color2
```
[*]Colors of selected text & background within the Grub2 menu border.
[*]Defaults to *color_highlight* settings if not specified.
[/LIST]


[*]**Non-selected entries within the Grub Menu Border (the rest):**
[LIST]
[*]```
menu_color_normal=color1/color2
```
[*]Colors of non-selected text & background within the Grub2 menu border.
[*]Defaults to *color_normal* settings if not specified.
[/LIST]


[*]**Highlighted Text Outside the Grub Border (one line):**
[LIST]
[*]```
color_highlight=color1/color2
```
[*]If there is no *menu_color_highlight* entry this setting is used within the Grub2 menu border for the selected entry line.
[/LIST]


[*]**Text/Colors Outside the Grub Border:**
[LIST]
[*]```
color_normal=color1/color2
```
[*]Colors of text & background outside the Grub2 menu border.
[*]If there is no *menu_color_normal* entry this setting is used within the Grub2 menu border for the non-selected areas.
[/LIST]
[/LIST]

An example is attached. The background image was a black screen with an Ubuntu logo. The image is visible within the menu border since both "menu_color..." entries have black as the second color. The image is not visible outside the menu box since the "color_normal" *color2* is not 'black' (transparent).

> menu_color_normal=white/black
menu_color_highlight=yellow/black
color_normal=blue/red
color_highlight=black/white    (Not illustrated)


**[COLOR="DarkRed"]Don't forget[/COLOR]** 

[LIST]
[*]You are just testing the settings at the Grub prompt/menu. Once you have settled on your color combinations, boot, make the changes to */etc/grub.d/05_debian_theme*, save the file.
[*]*update-grub* for the changes to be incorporated in *grub.cfg*.
[/LIST]

And yes, I know the attached example is not a good combination for ease of viewing, but it show different color combinations.

---

### Post by DarkDancer on 2011-04-02
Tried both ways, no background.... :(

---

### Post by ranch hand on 2011-04-02
> **DarkDancer said:**
> Tried both ways, no background.... :(
Do you have;
```

GRUB_BACKGROUND=/boot/grub/whatever.png

```
(or .jpg) in your /etc/default/grub file?

That was the problem I had.  I have been upgrading and not letting dpkg over write my old files and they had just gotten out of date.  That line has to be there, now, so that grub looks for an image.

---

### Post by DarkDancer on 2011-04-02
Thanks Ranch Hand, that got it... ;)

---

### Post by ranch hand on 2011-04-02
Wow.  I love it when my mistakes help someone else.

Glad that got it.

---

### Post by drs305 on 2011-04-02
> **DarkDancer said:**
> Tried both ways, no background.... :(

Glad you were able to get it working by using the GRUB_BACKGROUND setting. That means the image is valid and gfxterm is working.

The point of the thread though is that you should now be able to just drop an image into /boot/grub and not have to do anything other than update grub. 

Are you sure you are using Grub 1.99 (RC or later)? The entry works in prior G2 versions but the 'drag & drop' won't work in 1.98 or earlier.

---

### Post by DarkDancer on 2011-04-02
How do you tell?

---

### Post by ranch hand on 2011-04-03
```

sudo grub-install -v

```
I think the "sudo" is needed.  Here in Debian land I need ot be root to run that command.

---

### Post by DarkDancer on 2011-04-03
1.98+20100804-5ubuntu3

---

### Post by Anduu on 2011-04-03
Just a note...watch filenames.

I copied an image with spaces in the name and received an error during update-grub.

---

### Post by Harry33 on 2011-04-03
Just for additional info,
the latest grub (grub2 1.99~rc1-8ubuntu) upsets and totally or at least partially breaks Plymouth and the visibility of grub background.
The worst happens with proprietary drivers (no KMS), when Plymouth is lost completely during boot process.
This may or may not affect all graphics card models, however.

See more info from here:
[http://ubuntuforums.org/showpost.php?p=10629021&postcount=5](http://ubuntuforums.org/showpost.php?p=10629021&postcount=5)

---

### Post by Anduu on 2011-04-03
> **Harry33 said:**
> Just for additional info,
the latest grub (grub2 1.99~rc1-8ubuntu) upsets and totally or at least partially breaks Plymouth and the visibility of grub background.
The worst happens with proprietary drivers (no KMS), when Plymouth is lost completely during boot process.
This may or may not affect all graphics card models, however.

See more info from here:
[http://ubuntuforums.org/showpost.php?p=10629021&postcount=5](http://ubuntuforums.org/showpost.php?p=10629021&postcount=5)

Thanks for the heads up on that Harry.

---

### Post by drs305 on 2011-04-03
> **Anduu said:**
> Just a note...watch filenames.

I copied an image with spaces in the name and received an error during update-grub.

Anduu,

I tried it and does create an additional message during the grub update. 
> Generating grub.cfg ...
test: 151: n: unexpected operator
Found background image: .background_cache.png
Adding ...

It doesn't actually break grub, but makes a copy  of the image and names it *.background_cache.png* (note the hidden filename designation). The new image appears on boot and looks identical to the original image.

I suspect this is so a name which includes spaces doesn't break the system during boot and before the OS loads. 

The message certainly is not expected so I'll include a note about it in the original post. Thanks for pointing this out!

---

### Post by Anduu on 2011-04-03
> **drs305 said:**
> Anduu,

I tried it and does create an additional message during the grub update. 


It doesn't actually break grub, but makes a copy  of the image and names it *.background_cache.png* (note the hidden filename designation). The new image appears on boot and looks identical to the original image.

I suspect this is so a name which includes spaces doesn't break the system during boot and before the OS loads. 

The message certainly is not expected so I'll include a note about it in the original post. Thanks for pointing this out!

Strange...I received the "unexpected operator" error but no message about changing the name....

I didn't want to take the chance of something breaking so I renamed it manually and ran update-grub again.

---

### Post by jerrylamos on 2011-04-03
[QUOTE=ranch hand;10627986]
```

GRUB_BACKGROUND=/boot/grub/whatever.png

```

Ranch hand, that worked. Got rid of the Grub purple splotch.  

Now I still get the purple splotch with the login screen.  Any ideas?

Thanks, Jerry

---

### Post by cariboo on 2011-04-03
Just rename /usr/share/backgrounds/warty-final-ubuntu.png, then copy whatever picture that you have converted to a .png to the same directory, and rename it warty-final-ubuntu.png

---

### Post by ranch hand on 2011-04-04
> **cariboo907 said:**
> Just rename /usr/share/backgrounds/warty-final-ubuntu.png, then copy whatever picture that you have converted to a .png to the same directory, and rename it warty-final-ubuntu.png
That can't be the only thing anymore.  

I even deleted the original and that was a couple months ago.  Still have the same purple crap on the screen.

Beats me.  It would bother me if I had any intention of using the OS.

---

### Post by rbrick49 on 2011-04-04
> **ranch hand said:**
> I am simple.  Of coarse that would be the easy way to do it.  Also see the color on the image that you are using.

Give me another brain and you could probably call me a half wit.

Thanks.
well ranch hand I have 2 brains one is lost and the other one has gone looking for it now tell me why is ubuntu natty giving me a headache

---

### Post by ranch hand on 2011-04-04
> **rbrick49 said:**
> well ranch hand I have 2 brains one is lost and the other one has gone looking for it now tell me why is ubuntu natty giving me a headache
Well I am not a grumpy old man.  I, i will have you know, am a grumpy geezer.

I do not think that either of those are in the target group for Unity.  This is probably the problem.

---

### Post by ranch hand on 2011-04-04
I am having FUN with this version of grub.

It is not the version that is used by testing yet but that one is buggy and I don't think they are going to fix it (mainly some problem with uuid not working and having problems detecting the drive at times).

I just got mine from my alternate sources.list that only has sid main on it.  I just change the names to choose the one I want.  If I go to "sid"  I just get an update, install what I want, change the names back and update again to make sure I am not using sid anymore.

I think they may get this new grub to be really nice, at least for those of us with custom menus using the symbolic entries and not running any probes.

Probes are great for the first boot but I usually even chroot into a new install from the ISO and set up the menus and upgrade grub right then.

---

### Post by VanR on 2011-04-05
Tried both ways. No go. It won't let me drag-and-drop an image into /boot/grub or copy an image either. /etc/default/grub doesn't have the GRUB_BACKGROUND= line either, but it won't let me add it either. Guess I'll just forget it for now.

---

### Post by drs305 on 2011-04-05
> **VanR said:**
> Tried both ways. No go. It won't let me drag-and-drop an image into /boot/grub or copy an image either. /etc/default/grub doesn't have the GRUB_BACKGROUND= line either, but it won't let me add it either. Guess I'll just forget it for now.

VanR, since these are system files you have to do it as 'root'. If you want to move/copy via a file browser, open it with the following. 

```
gksu nautilus /boot/grub
```

You can also install a package called "nautilus-gksu" which will let you right click a folder in your normal browser and allow you to open it as administrator (root).

---

### Post by VanR on 2011-04-05
Thanks that worked great.

---

### Post by ranch hand on 2011-04-05
> **VanR said:**
> Thanks that worked great.
I would not be without nautilus-gksu on my box.  It is very handy.

Please remember that you are fooling around with your core files that run your OS.  You can, as root, do tremendous damage.  This can lead to an unusable OS.

You can also have a lot of FUN.

---

### Post by VanR on 2011-04-05
> **ranch hand said:**
> I would not be without nautilus-gksu on my box.  It is very handy.

Please remember that you are fooling around with your core files that run your OS.  You can, as root, do tremendous damage.  This can lead to an unusable OS.

You can also have a lot of FUN.

I'll remember that. I'm relatively new to Ubuntu. I ran 10.10 for a few months before deciding to try out 11.04. So far I'm having a ball.

---

### Post by ranch hand on 2011-04-05
If I am trying something new and exciting I usually have a second, small install (all my installs are on / and /home partitions) that I try things out on.

When I first installed Linux (Ubuntu 8.04) I got a little carried away with the power I suddenly had.  "Let's do this and see what happens."  The wife was not amused at me havig to reinstall 5 times in 7 days.  Unreasonable woman.  Thinks you should actually be able to USE the computer.

That is when I started my dual booting Hardy/Hardy.  We still have that 5th install and it still works fine.

---

### Post by VanR on 2011-04-05
> **ranch hand said:**
> If I am trying something new and exciting I usually have a second, small install (all my installs are on / and /home partitions) that I try things out on.

When I first installed Linux (Ubuntu 8.04) I got a little carried away with the power I suddenly had.  "Let's do this and see what happens."  The wife was not amused at me havig to reinstall 5 times in 7 days.  Unreasonable woman.  Thinks you should actually be able to USE the computer.

That is when I started my dual booting Hardy/Hardy.  We still have that 5th install and it still works fine.

I'm doing a dual boot Windows 7/ 11.04. My wife has her own computer so I do what I like with mine. I'm actually on the verge of building a new computer and leaving Windows for good. Don't want to pay for a new copy of Windows 7. Just trying to see if Ubuntu is gonna do it for me. So far I think it's golden, except for a few things I'll have to use my wife's computer for.

---

### Post by VanR on 2011-04-05
Got my GRUB background going, but it's mostly covered up by a big black square. How do I get rid of that black square? Got my font colors working nicely too.

---

### Post by drs305 on 2011-04-05
> **VanR said:**
> Got my GRUB background going, but it's mostly covered up by a big black square. How do I get rid of that black square? Got my colors working nicely too.

Experiment at the grub prompt.

Try setting the menu_color_normal to "color1/black". It sounds like it may be drawing a solid color within the menu box for some reason (even though black should be transparent). Press 'c' to get to the prompt, then 
```
menu_color_normal=white/black
```
Then ESC back to the menu and see if you can now see your image.

If not, try white/red or something to see if the now 'red' square is exactly the same size as the black box you were looking at. You could try the same with "color_normal=white/red"

---

### Post by VanR on 2011-04-06
> **drs305 said:**
> Experiment at the grub prompt.

Try setting the menu_color_normal to "color1/black". It sounds like it may be drawing a solid color within the menu box for some reason (even though black should be transparent). Press 'c' to get to the prompt, then 
```
menu_color_normal=white/black
```Then ESC back to the menu and see if you can now see your image.

If not, try white/red or something to see if the now 'red' square is exactly the same size as the black box you were looking at. You could try the same with "color_normal=white/red"

Nothing I did in the command line seemed to have any effect on the black box at all. I know the background is there, I get a flash of it for a split second, but most of the time the black box with the text in it is covering 90% it. For some reason the black is not transparent. It is black.

edit: I did manage to change the colors of the big black box using the command line, but returning it to black leaves it black again. I got a feel of how it works anyway.

edit again: Got it to work by removing the background jpg and replacing it with a different background. I don't know why but the first one wouldn't work.

---

### Post by manzdagratiano on 2011-04-06
> **drs305 said:**
> I knew the issue of font colors would come up eventually ...  ;-)

When the user specifies a custom background, the Grub devs decided to be conservative and specified a black/white font scheme. They were kind enough to comment on it in Step 7 of /etc/grub.d/05_debian_theme but left it to the user to figure out how to deal with the font colors when using custom backgrounds.

Whether you use the GRUB_BACKGROUND setting in /etc/default/grub or just stick an image in /boot/grub, here is a way to designate the colors.

First, keep in mind that Grub 2 considers *black* used as the second color entry as *transparent*. You will see the background image wherever *black* is the second entry (e.g. green/black = green text on transparent background).

To change the font colors, edit /etc/grub.d/05_debian_theme, around line 98:
```
gksu gedit +98 /etc/grub.d/05_debian_theme
```Add lines 2 & 3, using the colors you desire.

In this example, the highlighted line has a green font on a transparent background (i.e. there is no highlighted bar). The unselected text is light gray. If you want the highlighted text to have a colored bar across the screen, use a color other than ../black.

Save the file, then update Grub.
```
sudo update-grub
```

Thank you very very much Herr drs305! The new 05_debian_theme file is ***very*** different from the old one, and I would have been completely lost had it not been for your post. I believe the Grub2 Community Documentation also is in need of being heavily updated once Natty is officially released.

---

### Post by drs305 on 2011-04-06
> **manzdagratiano said:**
>  I believe the Grub2 Community Documentation also is in need of being heavily updated once Natty is officially released.

You are correct. I plan on rewriting the Community doc as soon as Natty is released to incorporate the changes brought about by 1.99. I'll probably update my Grub2 Basics thread first since that is just a forum entry and isn't 'licensed'.

[SIZE=4]This thread is now closed. The Natty Testing forum will be closing soon as Natty reaches its official release date.[/SIZE]

A new thread incorporating much of this information has been created in the Tips & Tutorials forum.
[Grub 2 Drop-In Backgrounds & Font Selection ]("http://ubuntuforums.org/showthread.php?p=10720685#post10720685")

---

