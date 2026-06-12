---
title: "CCSM Plugin by default"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Steel-Bunz on 2011-04-11
Hope it is not too late for a discussion.
 
Anyone thinks we should have CCSM plugin in the default install? And it should be integrated with system settings/appearance settings?
 
I know there is not much you can customize in Unity and I believe we should make it easier for the user to access whatever options available right now.

---

### Post by tjeremiah on 2011-04-11
yes, I think it should be there as default.

---

### Post by Rasa1111 on 2011-04-11
I think so to.

 I managed to change the settings for Unity using gconf-editor,
But was definitely thinking that CCSM should probably be there by default.

Especially for newbs who have no idea what theyre doing in gconf-editor.

---

### Post by nm_geo on 2011-04-11
At first blush I would agree it should be default.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-11
Definitely, it's basically the most obvious and straightforward way to edit the few settings you're able to edit in Unity.

---

### Post by Steel-Bunz on 2011-04-11
4 replies and 4 postive votes.. :-)
 
not sure how I pursue this idea. Will see if I can raise a feature request.. 
 
Please let me know if anyone knows the right way to pursue this.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-11
> **Steel-Bunz said:**
> 4 replies and 4 postive votes.. :-)
 
not sure how I pursue this idea. Will see if I can raise a feature request.. 
 
Please let me know if anyone knows the right way to pursue this.

Get a dev to add 'compizconfig-settings-manager' to the install script?

---

### Post by ELD on 2011-04-11
I also second this, integrate it with the new control panel.

---

### Post by umberstark on 2011-04-11
This is related to changing settings, therefore you'll be lucky to see it installed by default. 

Shuttleworth's goal is "zero-config experience"... yeah, don't laugh it's true.

---

### Post by mc4man on 2011-04-11
It's most unlikely natty will have anything, 11.10 probably
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739)

---

### Post by andrek on 2011-04-11
If they plan to stick with CD disk images then probably there won't be enough free space to have CCSM included..

---

### Post by Steel-Bunz on 2011-04-11
> **mc4man said:**
> It's most unlikely natty will have anything, 11.10 probably
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739)

Thanks. That explains it... 

Yeah, quite surprised by 'Zero config. experience' statement/decision by Mark Shuttleworth. Looks like the consensus is Unity is not mature enough for customization:p

I still believe basic options like icon size and launcher behavior should be visible to the users. Why else we have an option to change 'Appearance' of the Ubuntu in system settings? The zero config. experience rule can be applied there too.

---

### Post by Steel-Bunz on 2011-04-11
> **umberstark said:**
> This is related to changing settings, therefore you'll be lucky to see it installed by default. 

Shuttleworth's goal is "zero-config experience"... yeah, don't laugh it's true.

I honestly didn't expect those to be exact words from Shuttleworth.:D

---

### Post by PRC09 on 2011-04-11
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739/comments/2](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/748739/comments/2)

---

### Post by mc4man on 2011-04-11
When I filed that bug was bit surprised how completely it was shot down.
 I still think it's a mistake not to include a simple, _visible_ gui tool for whatever  unity plugin options are available at release and to set desktop size (I thought it was somewhat implied all the current ones may not be
I consider some of those options 'features' that should be advertised, not hidden.

They wouldn't even need to include ccsm or even a simple ccsm version, all those setting can be addressed by gconftool commands

( actually for anyone who knows how to make a simple gui app this would be a piece of cake to do, would expect some tweaking apps to arise.

---

### Post by Steel-Bunz on 2011-04-11
I agree with you, mc4man. If we can't guarantee a basic level of customization, Unity should wait until 11.10 to become default. I really hope Mark Shuttleworth didn't mean to aim for 'zero config. experience' in all of future Unity and Ubuntu. That doesn't sound like a good principle. If you read through his comments further down the bug report, customization options are equated to unnecessary code branch and even, bloat.

Sounds like iOS? :-)

---

### Post by Rasa1111 on 2011-04-11
Can someone elaborate on this "zero-config-experience"? 
I'm not quite understanding what that means?

thanks.

---

### Post by Steel-Bunz on 2011-04-11
> **Rasa1111 said:**
> Can someone elaborate on this "zero-config-experience"? 
I'm not quite understanding what that means?

thanks.

Natty will not include any config. tools to customize Unity. For example, you won't be able to change Launcher hiding behavior or Launcher Icon size without installing additional software.

---

### Post by mc4man on 2011-04-11
I actually don't take those 2 comments (2,14) too literally, though I guess time will tell.

Will be interesting to see if any of the 'experimental' options are removed for the release.

The only 2 I see as being real positives that could impact user experience are the Launcher icon size and backlight mode, the rest don't much matter
(w/ the icon size being by far the most important in that regard

And in general options not everyone will want a 2x2 desktop

---

### Post by Rasa1111 on 2011-04-11
> **Steel-Bunz said:**
> Natty will not include any config. tools to customize Unity. For example, you won't be able to change Launcher hiding behavior or Launcher Icon size without installing additional software.

Ok thank you Steel-Bunz. 

So now I am even more confused... lol

 I understand that one must install CCSM to change Unity options (with a GIU)..
But there is also gconf-editor, which i used to "customize" Unity last night. 

 and that requires no additional software. 

So is this just not something everyone is aware of? 
(being able to "customize" unity through gconf)

Or does shuttleworth also want this removed? lol

I was able to change the launcher hide behavior, backlighting, size, opacity, etc.

Not sure how much more the CCSM plugin allows,
but gconf-editor seemed to get done what I needed. 
Without installing CCSM. 

 thanks again.

---

### Post by umberstark on 2011-04-12
> **Rasa1111 said:**
> Ok thank you Steel-Bunz. 

So now I am even more confused... lol

 I understand that one must install CCSM to change Unity options (with a GIU)..
But there is also gconf-editor, which i used to "customize" Unity last night. 

 and that requires no additional software. 

So is this just not something everyone is aware of? 
(being able to "customize" unity through gconf)

Or does shuttleworth also want this removed? lol

I was able to change the launcher hide behavior, backlighting, size, opacity, etc.

Not sure how much more the CCSM plugin allows,
but gconf-editor seemed to get done what I needed. 
Without installing CCSM. 

 thanks again.

The idea of zero-config is that you don't* need* those options, because the best options will already be the default, so therefore customisation options don't need to be installed or shown to the user.

It's nice if you know to install dconf and ccsm, but not everybody does, and I'd wager not everyone likes the default size of the launcher icons (way *way* too big on either a netbook or full HD monitor imo) etc etc.

For those that don't know about ccsm or dconf (like new users), they shouldn't have to go searching the internet for the answer to something as basic as "hmm, these icons are a bit big, how do I resize them?".

It's not even that Zero-config is a noble goal to achieve: it's not.

---

### Post by Rasa1111 on 2011-04-12
> **umberstark said:**
> The idea of zero-config is that you don't* need* those options, because the best options will already be the default, so therefore customisation options don't need to be installed or shown to the user.

It's nice if you know to install dconf and ccsm, but not everybody does, and I'd wager not everyone likes the default size of the launcher icons (way *way* too big on either a netbook or full HD monitor imo) etc etc.

For those that don't know about ccsm or dconf (like new users), they shouldn't have to go searching the internet for the answer to something as basic as "hmm, these icons are a bit big, how do I resize them?".

It's not even that Zero-config is a noble goal to achieve: it's not.

 Oh Ok, I got ya now! 
Jeez. I agree, that is ridiculous. 

"the best options will already be default"..
"don;t need to be installed or shown"
wtf?
I don't care who it is.. that deserves a.. "and, you are who?" 
lol :rolleyes:

Seriously,
Now i understand some of the previous comments in the thread better.  lol

wow..
I thought it was rather hideous until learned how to change it.
Still not as pretty as I can get AWN, but better than it was by default. :o 

  Man...
Some people.... :???:

Thanks for the better explanation.
much appreciated. :)

---

### Post by MightyMouse on 2011-04-12
[PHP]The idea of zero-config is that you don't* need* those options, because the best options will already be the default, so therefore customisation options don't need to be installed or shown to the user.[/PHP]

And this is exactly the problem. This reminds me of a certain B. Gates who also had the idea that he knew best and all the kids have to just follow him. Ubuntu should allow every user to customize the system to his/her needs and not pretend to 'know what's best' for the user. 

[PHP]It's nice if you know to install dconf and ccsm, but not everybody does, and I'd wager not everyone likes the default size of the launcher icons (way *way* too big on either a netbook or full HD monitor imo) etc etc.[/PHP]

Even with ccsm there still is very little to customize to be honest. Many fans of the old panel-layout just want the liberty to change how their desktop looks like and which programs/applications they consider important or not. I don't say we have to go back or keep the classic desktop (since it seems it is not Ubuntu’s but Gnomes choice to discontinue the old-style panel) but think that Unity has to listen to what the users want and if that requires them to come up with something that looks and feels like a panel with lot's of options for users to tweak than they should simply get to work and make it happen.


[PHP]For those that don't know about ccsm or dconf (like new users), they shouldn't have to go searching the internet for the answer to something as basic as "hmm, these icons are a bit big, how do I resize them?".

It's not even that Zero-config is a noble goal to achieve: it's not.[/QUOTE][/PHP]

AT least IMHO.

---

### Post by Rasa1111 on 2011-04-12
> **MightyMouse said:**
> And this is exactly the problem. *This reminds me of a certain B. Gates who also had the idea that he knew best and all the kids have to just follow him.* Ubuntu should allow every user to customize the system to his/her needs and not pretend to 'know what's best' for the user. 

 Absolutely. 
I thought the same thing. 
:KS for you. lol <3

Rather alarming..
To me anyway..
I always thought he was a "cool" guy.. :???:

 How anyone can tell anyone else what 'works best for them' is beyond me. These people have serious problems. 

 "This is what [SIZE="4"]I[/SIZE] think is best, So that is what everyone should and must use!"

What? 

> Even with ccsm there still is very little to customize to be honest. Many fans of the old panel-layout *_just want the liberty to change how their desktop looks like and which programs/applications they consider important or not. I don't say we have to go back or keep the classic desktop (since it seems it is not Ubuntu&#8217;s but Gnomes choice to discontinue the old-style panel) but think that Unity has to listen to what the users want and if that requires them to come up with something that looks and feels like a panel with lot's of options for users to tweak than they should simply get to work and make it happen._*


 These have been my thoughts from the start,
Only you have put it far better than I have managed to so far. lol :???: :/
 Thanks!
 Great post! <3 :KS

---

### Post by lucazade on 2011-04-12
> Even with ccsm there still is very little to customize to be honest. Many fans of the old panel-layout just want the liberty to change how their desktop looks like and which programs/applications they consider important or not. I don't say we have to go back or keep the classic desktop (since it seems it is not Ubuntu’s but Gnomes choice to discontinue the old-style panel) but think that Unity has to listen to what the users want and if that requires them to come up with something that looks and feels like a panel with lot's of options for users to tweak than they should simply get to work and make it happen.

In a 6 months work a developer should focus on core stability and minimal options, mostly because a shell should be rocksolid and without memory leaks.
When you reach stability and core functions working you can think about options and customizations.
To me it is the natural way of coding!

---

### Post by MightyMouse on 2011-04-12
[PHP]In a 6 months work a developer should focus on core stability and minimal options, mostly because a shell should be rocksolid and without memory leaks.
When you reach stability and core functions working you can think about options and customizations.
To me it is the natural way of coding![/PHP]

Sorry if I sounded like I do not appreciate all the work that is done by you guys!! Far from, I just see that everybody is loving/hating Unity or classic when I feel the discussion is not about the one or the other but rather that it feels like the user is considered a 'threat' to the perfect default setting (and don't take this too literal). I think that what most people discussing this want is to hear that their wishes are taken seriously. I have read several comments (in several different threads) that made me feel like those that are strong supporters of Unity think that the user has to change to accommodate the software (and as I said, that was what drove a lot of people away from windows) rather, then the other way around.
Maybe if there was a little more willingness on both sides to not just crash and trash other users preferences but more constructive discussion on how to find a way to get the best of both worlds we could all help to keep Ubuntu a place where everybody can get what they want.

Maybe we should start a thread with a less 'dividing' subject title, not the typical 'Do you like or hate Unity' and 'Will you leave if there is no classic desktop any longer' but maybe something in the line of 'Which functions are essential for Unity to work for you?'.

Cheers, and thanks to all the developers, you do a great job and you need our feedback to make us love your programs even more.

---

### Post by lucazade on 2011-04-12
> **MightyMouse said:**
> [PHP]In a 6 months work a developer should focus on core stability and minimal options, mostly because a shell should be rocksolid and without memory leaks.
When you reach stability and core functions working you can think about options and customizations.
To me it is the natural way of coding![/PHP]

Sorry if I sounded like I do not appreciate all the work that is done by you guys!! Far from, I just see that everybody is loving/hating Unity or classic when I feel the discussion is not about the one or the other but rather that it feels like the user is considered a 'threat' to the perfect default setting (and don't take this too literal). I think that what most people discussing this want is to hear that their wishes are taken seriously. I have read several comments (in several different threads) that made me feel like those that are strong supporters of Unity think that the user has to change to accommodate the software (and as I said, that was what drove a lot of people away from windows) rather, then the other way around.
Maybe if there was a little more willingness on both sides to not just crash and trash other users preferences but more constructive discussion on how to find a way to get the best of both worlds we could all help to keep Ubuntu a place where everybody can get what they want.

Maybe we should start a thread with a less 'dividing' subject title, not the typical 'Do you like or hate Unity' and 'Will you leave if there is no classic desktop any longer' but maybe something in the line of 'Which functions are essential for Unity to work for you?'.

Cheers, and thanks to all the developers, you do a great job and you need our feedback to make us love your programs even more.

I agree with your suggestion about a thread in the line of which functions are essential... this seems to me a good and appreciable approach!

ps I'm not an ubuntu dev.. only a linux enthusiast ;)

---

### Post by Merk42 on 2011-04-12
> **MightyMouse said:**
> Ubuntu should allow every user to customize the system to his/her needs and not pretend to 'know what's best' for the user.Even if everything were customizable (which I'm a fan of). Ubuntu would still need to pick a default behavior, so finding out "the best options" would still be something they'd need to do.

Unrelated, could you use [quote] instead of [PHP] so it wasn't multicolored with scrollbars?

---

### Post by seeker5528 on 2011-04-13
I install CCSM for my own use, just because there is not a better option for some of the configuration, but....

For the size of the icons on the launcher panel I would rather just be able to grab the edge of the panel and drag it to the size I want instead of having to use a configuration option.

For other things, instead of including CCSM, I would rather see a look and feel kind of gnome-control-center applet for Unity that provides a subset of what you can enable/disable/configure in CCSM and presents the options in a more sane/descriptive way. 

By subset I primarily mean not showing you an option to enable plugins that provide the same function as a plugin that is enabled by default and uses the same keybindings.

If there was an option in CCSM to treat plugins that serve the same purpose as mutually exclusive, resulting in the user being asked if they want to disable the existing plugin and continue or cancel and continue using the existing plugin, and that option was enabled by default, that would be a big improvement, IMHO, but that still leaves you down a rabbit hole of plugins with names and descriptions that leave you unsure of what they provide with options that don't make the picture any clearer.

Later, Seeker

---

### Post by cariboo on 2011-04-13
@seeker5528, try Alt-F2 and type:

```
about:config
```

---

### Post by seeker5528 on 2011-04-13
That's good if you are helping someone with Unity specific options and don't want to drag them through the entire CCSM panel to get to the Unity plugin.

But there is other stuff.....

There is nothing in the name or description of the scale plugin that gives me a clue that disabling it kills the nice view you get of an application's open windows when you double click an icon on the launcher bar of an app with multiple open windows. And because of this it's probably not an option you want to float in front of people.

Without knowing what the relationship of the scale plugin is to Unity, it's pretty much an accident to figure out that enabling 'Scale Addons' will provide the additional function while viewing an application's open windows of allowing you to zoom the windows in and out with a right click and close windows with a middle click. But if there was Unity specific configuration provided, it could be presented to people in a way more descriptive to what it does relative to Unity and without having to expose the option to disable the scale plugin.

There are multiple application switcher plugins. They all default to 'Alt'+'Tab'. They are not technically mutually exclusive, so it's not an error that people should be allowed to have more than one of these enabled at a time, but it seems unlikely that anybody but and advanced user would really want to change the key bindings on one or more of these so they can have more than one enabled and keyboard accessible at the same time. If there was Unity specific configuration for this, it could be offered to people as an 'either, or, or' choice and advanced users could still install and use CCSM if, for some reason, they actually want more than one switcher enabled.

Later, Seeker

---

