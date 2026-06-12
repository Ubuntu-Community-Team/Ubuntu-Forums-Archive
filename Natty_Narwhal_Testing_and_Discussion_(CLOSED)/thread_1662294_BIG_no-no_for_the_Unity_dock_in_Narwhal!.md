---
title: "BIG no-no for the Unity dock in Narwhal!"
date: 2011-01-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by JuicyCouture on 2011-01-07
anyone else notice how they decided to extend the already ugly grey background behind the icons - ALL the way down to the bottom of the screen?


no way that makes it in to the final release. the background should only go as far as the icons - otherwise you're just blacking out this big chunk of screen space for no reason, all the way to the little trash bin - which could just go at the end of the last icon.

so you have this big chunk of screen black/grey'd out by default in the unity desktop? 

really ugly, i wouldnt have a solid background behind the icons to begin with - but that just makes it worse. 

no WAY that can be left by default

i made a suggestion for it here if any of you know/are a mod there to get it pushed up.

[http://brainstorm.ubuntu.com/idea/26914/]("http://brainstorm.ubuntu.com/idea/26914/")

---

### Post by Amaranth on 2011-01-07
Yeah, I doubt that change is going to be made. The dock has always extended down that far, I suspect it is a decision from the design team. I think it looks better this way anyway but then again I have 9 app icons, the workspace switcher, and the trash so it's almost full.

---

### Post by efflandt on 2011-01-07
Are you new to Natty (which is under development and far from being finalized)?  If things are working properly (which has been intermittently in my case), the Unity panel is translucent.  And if you install Compiz Config Settings Manager (CCSM) you can click on the Unity icon in that and check **Autohide Launcher**.  Then if you have any window full screen, the panel auto hides.  If you want it to appear, you move your cursor to upper left corner.

But it does not really take up much space on a 32" widescreen 1080p HDTV used as a monitor.

---

### Post by JuicyCouture on 2011-01-07
i know in ubuntu especially theres always the option to change and customize - i just meant for the default out of the box user experience.

i also dont like how its on the left side of the screen but i guess i could get used to that - kind of changed everything to a 4:3 aspect ratio (im running on a smaller screen, i know on a big monitor im sure its hardly noticeable)

---

### Post by JuicyCouture on 2011-01-07
so if they're making this the new standard for regular ubuntu - are they just gonna toss out kubuntu?

---

### Post by kostkon on 2011-01-07
> **JuicyCouture said:**
> so if they're making this the new standard for regular ubuntu - are they just gonna toss out kubuntu?
No. The obvious answer is :P

Kubuntu will continue to use KDE whereas Ubuntu will use the new gnome-based Unity desktop environment.

---

### Post by JuicyCouture on 2011-01-07
derp

i better be able to make that tasbar see through

---

### Post by cariboo on 2011-01-08
There is someone that frequents this sub-forum that has 20 icons in the panel, and personally at the moment I have 16.  there is just enough space at the bottom for one more icon, then the color of the background is irrelevant.

> derp

i better be able to make that tasbar see through

If not, then what?

---

### Post by JuicyCouture on 2011-01-08
> **cariboo907 said:**
> There is someone that frequents this sub-forum that has 20 icons in the panel, and personally at the moment I have 16.  there is just enough space at the bottom for one more icon, then the color of the background is irrelevant.



If not, then what?


off myself i imagine

---

### Post by cecilpierce on 2011-01-08
If you don't like it you can logout and choose 'Ubuntu Classic Desktop' down on the bottom of the screen and log back in to the old style Gnome desktop. :confused:

---

### Post by jerrylamos on 2011-01-08
> **JuicyCouture said:**
> i know in ubuntu especially theres always the option to change and customize

Juicy, not any more.  Ubuntu comes with Unity, like it or not.  "Unity" doesn't even run on three of my four pc's.  The developers view "classic" as temporary while they work on "Unity".

Ubuntu has kicked the gnome developers out.  Read the Ubuntu developers posts
[http://www.h-online.com/open/features/Ubuntu-and-the-price-of-Unity-1156110.html](http://www.h-online.com/open/features/Ubuntu-and-the-price-of-Unity-1156110.html)

Ubuntu is being specifically targeted to "Newbie" user with "high end 3D graphics".  Only.

Even on my big screens I fill them with my applications.  I'm not about to give up that much valuable real estate to Unity, so I don't even run it on my one pc where it will work.  I do test it.  So far at Alpha level my impression is more keystrokes, more windows, more mouse pointer and less function than gnome.  It's all about "Unity eye candy" and not about applications.  Applications are what I run lunux for.  

"Unity" is a "Unilateral" decision from the top.  He who has the money makes the decisions.

Jerry

---

### Post by Amaranth on 2011-01-08
Oh come on, at least try to learn the facts before spewing this crap. The goal of Unity is to make things easier for a new user, yes. That doesn't mean it neglects the poweruser, a good UI should scale up with the user. Unity may not do so now or even when natty is final but that doesn't mean it isn't the plan.

As far as system requirements, right now compiz itself needs almost nothing as far as graphics, just something that accelerates a bare minimum of OpenGL. nux and unity build on top of that and iirc raise the requirements slightly over that but any GPU better than an intel 845 should have no problems other than driver issues or nux/unity bugs.

And the classic mode will be around as long as GNOME maintains it. The only part we've "kicked out" is gnome-shell and once we switch to a GNOME 3 stack that will even be available for you to install. gnome-shell has the same or higher requirements as compiz/nux/unity and requires the same fallback to the classic mode when you don't have sufficient hardware or don't like how it works.

---

### Post by lucazade on 2011-01-08
> **jerrylamos said:**
> Juicy, not any more.  Ubuntu comes with Unity, like it or not.  It doesn't even run on three of my four pc's.  The developers view "classic" as temporary while they work on Unity.

Ubuntu comes with Unity and with the classic GNOME panel so they haven't removed anything.. 
they just added a new shell because GNOME panel is no more developed and GNOME Shell is not ready for prime time and doesn't integrate any of Ubuntu latest software (indicator, notifyosd...)

> **jerrylamos said:**
> Ubuntu has kicked the gnome developers out.  Read the Ubuntu developers posts (I'll try to find the links)

This is not true and has been said a lot of times, 
Canonical asked to GNOME guys to accept their stuff upstream.. 
so it looks like the opposite to me.

> **jerrylamos said:**
> Ubuntu is being specifically targeted to "Newbie" user with "high end 3D graphics".  Only.

Ubuntu is targeted to any user: devs and newbies with any kind of hw support (old gfx card will use classic desktop)

> **jerrylamos said:**
> Even on my big screens I fill them with my applications.  I'm not about to give up that much valuable real estate to Unity, so I don't even run it on my pc where it will work.  I do test it.  So far at Alpha level my impression is more keystrokes, more windows, more mouse pointer and less function than gnome.  Not for me.

Looks to me like "Unity" is a "Unilateral" decision from the top.  He who has the money makes the decisions.

Jerry

This is about tastes, I like how Unity is growing and I share their decisions.
We should wait for a final release because Unity has been rewritten from scratch only 3/4 months ago.

---

### Post by jerrylamos on 2011-01-08
> **lucazade said:**
> This is about tastes, I like how Unity is growing and I share their decisions.


lucazade, there's a bunch more on "Ubuntu and the price of Unity", see:

[http://www.h-online.com/open/features/Ubuntu-and-the-price-of-Unity-1156110.html](http://www.h-online.com/open/features/Ubuntu-and-the-price-of-Unity-1156110.html)

To quote:

"... make Ubuntu ... popular among the kinds of user who have never heard of free software before."

Now, what about the rest of us ordinary users who are past the "Newbie" stage?

Jerry

---

### Post by JOHNNYG713 on 2011-01-08
Never fear Gnome is here and will be available at log in ! No one is going to force the use of "unity" ! Just take a deep breath ! Unity is not final yet !  and still being developed ! Give it a chance ! They are just trying to be Unique and forge a new type of interface ! Relax ! :D

---

### Post by Merk42 on 2011-01-08
That whole h-online article is so biased
GNOME complains that Canonical is branching off, then the very next paragraph explains GNOME's origins **breaking off from KDE**
Also I don't see why GNOME is all upset about Canonical using Unity, does GNOME get upset when a distro uses Shotwell instead of F-Spot, Pidgin instead of Empathy, Firefox instead of Epiphany?


Back to the topic of the thread, the panel currently is translucent.
I'm curious, why exactly would you not want it to extend, from a usability standpoint? Any windows either A) wouldn't extend that far left (by default) or B) would extend that far if the entire dock were auto/intellihidden.

---

### Post by mc4man on 2011-01-08
There's no loss of function or space w/ the launcher extending top to bottom,, fine the way it is.
> 
This is about tastes, I like how Unity is growing and I share their decisions.
We should wait for a final release because Unity has been rewritten from scratch only 3/4 months ago. 
A big + 1 - I like unity, don't consider it "Newbie"  only, if you don't like then don't use it or use your non-"Newbie" smarts to make it work for you.

I do hope they follow thru on a true-hide option, if not, at least atm. the parameter is clearly exposed and easy to enable.

---

### Post by Nickedynick on 2011-01-08
I'm just going to throw my opinion in here, whether it's welcome or not:

The devs are producing this all with no cost to the end user. We should all think about that a bit more before whining about every minor thing that upsets us about the direction of future releases.

If Natty is going to be that much of an issue for you, then stay with Maverick until things are sorted out so that you *can* do what you want with it. It's not going anywhere, and it'll still be supported.

---

### Post by amano on 2011-01-08
Well spoken. And Canonical is not going to take anything away. The Classic Gnome panel will stay and even GNOME Shell will be delivered (even if it should be delayed to October for technical reasons).

Canonical is throwing in Unity into the whole open source and libre pool (yes, for us!) and isn't taking anything away (Gnome Panel, AWN, Docky and in future GNOME Shell will stay). They just broaden the options for us users to choose from...

---

### Post by Mr. Picklesworth on 2011-01-10
*oops* :)

---

### Post by Mr. Picklesworth on 2011-01-10
I'll just point out that the art assets are effectively placeholders. Visual design can and will change later in the cycle.

(Which is why I haven't started babbling about how lavish gradients — like we have on the top panel — should all die in a fire)

---

### Post by JuicyCouture on 2011-01-10
> **Mr. Picklesworth said:**
> I'll just point out that the art assets are effectively placeholders. Visual design can and will change later in the cycle.

(Which is why I haven't started babbling about how lavish gradients — like we have on the top panel — should all die in a fire)

what is.....THAT....

---

