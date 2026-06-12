---
title: "Oneiric Ocelot (11.10) will not have Ubuntu Classic Desktop"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-04-03
This is what Mark Shuttleworth is thinking now.
Read it from his comment on the bug 739812:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/739812/comments/5](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/739812/comments/5)

---

### Post by beameup on 2011-04-03
Sounds like an ambitious goal, and probably the best way to go.

Hey who knows, maybe we'll see a true Gnome specific variant one day :P

---

### Post by davepoth on 2011-04-03
Well that's alright, because 11.10 probably won't have me.

---

### Post by PaulW2U on 2011-04-03
> **beameup said:**
> maybe we'll see a true Gnome specific variant one day :P
**G**ubuntu? :lolflag:

---

### Post by lucazade on 2011-04-03
I've tried to remove gnome-panel on Natty installation to see what happen

package removed:
gnome-applets
gnome-panel
gnome-panel-bonobo
gnome-panel-data
indicator-applet
indicator-applet-appmenu
indicator-applet-complete
indicator-applet-session

Unity3D and 2D still working good, only a "Classic Session" item in GDM menu.. probably gnome-session handles this.

We'll see for Oneiric..

---

### Post by MacUntu on 2011-04-03
No surprise. 2D should have been the fallback for Natty, didn't work, so it's planned for Oneiric.

---

### Post by madjr on 2011-04-03
before crazy people come in, just want to say that **nothing is written in stone**. It's just "assumed" that unity will be **matured and flexible enough** by then (still 7+ months left, so lots can happen).

and all they want to really get rid of is the old gnome-panel, nothing else.

I've also already seen "unofficial" patches to change the position of the launcher too. Who knows maybe they'll include them soon.

and if the majority still not satisfied with unity by October and still use the old desktop, then am sure they can postpone removing gnome-panel at least till 12.04

So, like i said, is just assumed that the majority will had moved to unity by then and not use old gnome (so is logical to remove it to save space and other reasons)

and **G**ubuntu doesn't sound like a bad idea either

---

### Post by rapiertg on 2011-04-03
Mark's statement don't mean it will not be included in repos. Don't see a problem...
```
sudo apt-get install gnome-panel
```
And your back with our beloved panels again.

---

### Post by dino99 on 2011-04-03
we have to wait for gnome3 first to know the latest changes/fixes

---

### Post by kansasnoob on 2011-04-03
Mark goes on to say:

> **[COLOR="Red"]11.04 was designed for desktops, not tablets[/COLOR]**, there are a number of
profound changes in apps needed to get the libre desktop running nicely
on a tablet.

That seems a bit odd to me, but regardless I'm not worried. Why?

#1. Lubuntu is looking like a truly reasonable alternative.

#2. Xubuntu is also very good, it's just a matter of preference.

#3. I still find Kubuntu a bit bloated compared to gnome 2.3*, but compared to gnome3 w/gnome-shell I don't think that argument sells anymore. I do rather wish we had a KDE-lite version similar to that offered by Aptosid.

#4. For as long as I can remember the package "gnome-desktop-environment" has been in the repos. Yes it's only gnome version 2.30, whereas we currently use 2.32, but that's still the version used in Squeeze and Debian-testing so it's hardly prehistoric. It installs on an Lubuntu base like a snap and the blue Debian scheme fits in almost perfectly with the Lubuntu splash. I could write a book on this :)

#5. Linux Mint says they're going to use Gnome3 with their common single lower panel in their next release. This should be interesting since that version will be based on Ubuntu 11.04 AFAIK, but w/gnome3. I'm curious to see what they actually come up with. (Not that I'm likely to change distros because I find many of Mint's tools not to my liking).

#6. The Fedora 15 alpha released w/gnome3 with the intent of staying gnome-shell only but they've now added an option to use the old panel arrangement. I'll grant you it's a mess IMHO, but it's very early in development. (Here again it's very doubtful that I'd switch to Fedora)!

Going back to that bug report I have to point out that Mark also asked:

> Why is this critical, Brian?

I can't help but remember an exchange I had with Mark and others at Ayatana about notify-osd. While most were concerned about position, I was more concerned about the duration notifications are displayed.

I'm visually impaired so I prefer to have notifications wait forever until I respond, therefore I requested a gui be added to allow for that but my idea was poo-pooed because such a gui would create bloat.

Now that's not surprising and I'm certainly not saying that Mark just doesn't care. It's impossible for any one distro to be 100% user friendly to every potential user.

Vinux is based on Debian & Ubuntu and it does a really good job of improving usability for the visually impaired. I just prefer starting with some flavor of Ubuntu and working my way up to what satisfies me.

NOTE: It's also possible to create an Adriane Knoppix live-usb for someone who's truly blind. It's a neat little pocket OS that allows the blind to use virtually any computer that'll boot Debian from USB :D

Finally, I expect that the change to gnome3/gnome-shell/unity will actually spark a lot of innovation, and almost undoubtedly some new Ubuntu "children". Anyone up for a Retro-buntu :lolflag:

---

### Post by ronacc on 2011-04-03
alas poor Oneiric I'll never get a chance to know ye well .

---

### Post by ikt on 2011-04-03
> **kansasnoob said:**
> I'm visually impaired so I prefer to have notifications wait forever until I respond, therefore I requested a gui be added to allow for that but my idea was poo-pooed because such a gui would create bloat.

The source is open, why don't you make the gui yourself?

---

### Post by ronacc on 2011-04-03
> **ikt said:**
> The source is open, why don't you make the gui yourself?

Why should he have to ? GS is the direction Gnome is going ,Ubuntu is based on Gnome , Why should I have to compile GS for myself (as I have been doing since Maveric ) , When it becomes guite plain that Ubuntu will no longer be My stable system what incentive do I have to continue to participate ?

---

### Post by kansasnoob on 2011-04-03
> **ikt said:**
> The source is open, why don't you make the gui yourself?

Duh? Seriously!

Because I'm old and legally blind and I couldn't write enough code to refill the toilet paper spool!

Are we going to revisit the, "you shouldn't use Linux unless you know how to code crap"??????

I realize my comment is harsh, but so is yours!!!!!!!!!!!!

If you can't digest the thought of an end user actually appreciating Linux then I'm wasting my time!!!!!!!!!!!!!!!!!!!

---

### Post by PatrickVogeli on 2011-04-03
well, actually didn't say we won't get classic desktop, just that the fallback for unity 3d will change to unity 2d.

I don't think there's much to worry about... apt will be there to install our beloved classic desktop!

---

### Post by ikt on 2011-04-03
> **ronacc said:**
> Why should he have to ?

Because no program is available and there is no intention to make such a program available, there's a gap for us to fill.

> **kansasnoob said:**
> Duh? Seriously!

Because I'm old and legally blind and I couldn't write enough code to refill the toilet paper spool!

No excuses!

> **kansasnoob said:**
> 
Are we going to revisit the, "you shouldn't use Linux unless you know how to code crap"??????

I realize my comment is harsh, but so is yours!!!!!!!!!!!!


Is your comment harsh? :confused:

Anyway I agree, you shouldn't have to know how to code to use linux, I'm just suggesting there is a gap here to fill.

> **kansasnoob said:**
> 
If you can't digest the thought of an end user actually appreciating Linux then I'm wasting my time!!!!!!!!!!!!!!!!!!!

End users do appreciate ubuntu, it's why it's the most popular linux desktop distro, in your particular situation the need for more customisation is required, just like my situation, which is why I was hoping you could code, so we can code together to fill in the gaps, doesn't matter, thanks anyway.

---

### Post by VMC on 2011-04-03
> **PatrickVogeli said:**
> well, actually didn't say we won't get classic desktop, just that the fallback for unity 3d will change to unity 2d.

I don't think there's much to worry about... apt will be there to install our beloved classic desktop!

unity 2d will be an interesting fallback instead of gnome. Not that I like or dislike about unity 2d - haven't tried it. It will just be interesting to see a gnomeless ubuntu.

---

### Post by madjr on 2011-04-03
> **VMC said:**
> unity 2d will be an interesting fallback instead of gnome. Not that I like or dislike about unity 2d - haven't tried it. It will just be interesting to see a gnomeless ubuntu.

i think you mean gnome-panel-less

---

### Post by jerrylamos on 2011-04-03
> **MacUntu said:**
> No surprise. 2D should have been the fallback for Natty, didn't work, so it's planned for Oneiric.

2D working fine for me, loaded from Synaptic.

What keeps crapping out and crashing on 3D Beta is Compiz of course, on my two pc's that have the required hardware.  

My three medium and older pc's run Natty 2D fine, even a 10 year old IBM Thinkpad.

My guess, Compiz and 3D were too fat for 2D to also fit on the CD.

My opinion, preferable for Natty to have gone out with 2D so it would run on all the pc's, then have 3D available for download for the newest hardware.

The Market will decide.

Jerry

p.s. I'm not a Unity fan, I just run it looking for Alpha/Beta bugs.

---

### Post by Merk42 on 2011-04-03
Oh boy, it's started! People are 'blaming' Canonical for getting rid of something **that will eventually be discontinued by its creators, GNOME**.
Guess what? If Unity never existed, we would STILL be in this situation eventually. (though does GNOME 3 even have a 2D Shell fallback?)
> **beameup said:**
> Hey who knows, maybe we'll see a true Gnome specific variant one day :P
I'll be pedantic and say that Unity is GNOME, and "Shubuntu" (ie Shell-buntu) would be a more accurate version name.

---

### Post by smellyman on 2011-04-03
> **Merk42 said:**
> Oh boy, it's started! People are 'blaming' Canonical for getting rid of something **that will eventually be discontinued by its creators, GNOME**.
Guess what? If Unity never existed, we would STILL be in this situation eventually. (though does GNOME 3 even have a 2D Shell fallback?)
 
I'll be pedantic and say that Unity is GNOME, and "Shubuntu" (ie Shell-buntu) would be a more accurate version name.
 
 
+1. 
 
I don't get the hysteria....

---

### Post by ronacc on 2011-04-03
what exactly is hysterical about personal preference ? Those of us who happen not to like Unity for whatever reason that we find good and sufficient ,are not lapsing into fits of hysteria but usually state our reasons in a calm and thoughtful manner .

---

### Post by cariboo on 2011-04-03
Could we please keep this on topic. Let's keep personalities out of this.

One thing I'd like to say it that Ubuntu is a meritocracy, if you don't like the way something is going, you can change it if you are willing to work for it. The installer is one good example, if nobody  had taken the effort to get some things changed, we'd have had a much different and in my opinion worse experience than we do now.

I'd personally like to thank kansasnoob for all the hard work he's put in on ubiquity and the boot info script. It just goes to show that if your willing to do the work, things can and will change.

---

### Post by beameup on 2011-04-04
> **Merk42 said:**
> Oh boy, it's started! People are 'blaming' Canonical for getting rid of something **that will eventually be discontinued by its creators, GNOME**.
Guess what? If Unity never existed, we would STILL be in this situation eventually. (though does GNOME 3 even have a 2D Shell fallback?)

I'll be pedantic and say that Unity is GNOME, and "Shubuntu" (ie Shell-buntu) would be a more accurate version name.

Hope you didn't misinterpret my post there. That was pure sarcasm. 
The line above that you didn't quote is how I really feel:
"Sounds like an ambitious goal, and probably the best way to go."

---

### Post by ronacc on 2011-04-04
> **Merk42 said:**
> Oh boy, it's started! People are 'blaming' Canonical for getting rid of something **that will eventually be discontinued by its creators, GNOME**.
Guess what? If Unity never existed, we would STILL be in this situation eventually. (though does GNOME 3 even have a 2D Shell fallback?)

I'll be pedantic and say that Unity is GNOME, and "Shubuntu" (ie Shell-buntu) would be a more accurate version name.

we are not "blaming " cononical for getting grid of "classic" that is in the cards anyway , What we are "blaming" canonical for is pushing unity to the exclusion of the "mainline" developement of Gnome (GS) . That they are doing so when it is obvious that Unity is at best a controversial and divisive path .

---

### Post by Merk42 on 2011-04-04
> **ronacc said:**
> we are not "blaming " cononical for getting grid of "classic" that is in the cards anyway , What we are "blaming" canonical for is pushing unity to the exclusion of the "mainline" developement of Gnome (GS) . That they are doing so when it is obvious that Unity is at best a controversial and divisive path .You personally know better, but there are a lot of people that blame Canonical for getting rid of GNOME 2.X/ aka panels.

I think their misunderstanding comes down to people unfamiliar with the differences between who makes what and Canonical's earlier adoption of Unity as a default UI vs other distro's adoption of GNOME Shell as default.

---

### Post by hugmenot on 2011-04-04
And I blame both Gnome and Canonical for not caring about people who are completely fine with their gnome-panly experience and don’t want to change in any way. They may want iterative improvements to apps, but not a {new,ill-conceived,overly fancy} desktop experience.

They should make sure gnome-panel get’s maintained, it get’s ported to GTK3, it is easily selectable as the user’s preferred session, it will be supported for at least two more years.

---

### Post by zika on 2011-04-04
If it is true that Unity will be compulsory, even though I could even than use Fluxbox, that might be a really tough decision for me, personally... Will see, but...
Why? Because Unity is not working on my machine, yet... Simple and clear, I can not do nothing wit it. Unity-2d, Classic Desktop, Fluxbox, all work as they have worked never before...
So, there is no future in Ubuntu for me, it seems... I'm really sorry to hear that...

---

### Post by sgage on 2011-04-04
I really wish people would use the correct terminology. Gnome 3 is NOT the Gnome Shell. Gnome 2 is NOT panels. Gnomes 2 and 3 are the underlying plumbing, while panels, Gnome Shell, Unity, etc. are shells on top of Gnome.

The Gnome Project has already stated that the panels will continue to be available for the Gnome 3 stack. So officially, The Gnome Project will offer a choice of Gnome Shell or Panels with Gnome 3.

I'm sure Unity will sit on the Gnome 3 stack eventually. 

In any case, panels will be available well into the glorious Gnome 3 future :KS

---

### Post by zika on 2011-04-04
> **sgage said:**
> I really wish people would use the correct terminology. Gnome 3 is NOT the Gnome Shell. Gnome 2 is NOT panels. Gnomes 2 and 3 are the underlying plumbing, while panels, Gnome Shell, Unity, etc. are shells on top of Gnome.

The Gnome Project has already stated that the panels will continue to be available for the Gnome 3 stack. So officially, The Gnome Project will offer a choice of Gnome Shell or Panels with Gnome 3.

I'm sure Unity will sit on the Gnome 3 stack eventually. 

In any case, panels will be available well into the glorious Gnome 3 future :KSI'm glad to hear that and I thank You for this correction. Future will show itself...

---

### Post by dino99 on 2011-04-04
> **zika said:**
> I'm glad to hear that and I thank You for this correction. Future will show itself...

only remove the metapackage and you will be free to uninstall all the eyecandy stuff you dont like/need

---

### Post by galacticaboy on 2011-04-04
> **PaulW2U said:**
> **G**ubuntu? :lolflag:
Gubuntu made me remember the old distro Gobuntu. Good stuff!

---

### Post by zika on 2011-04-04
> **dino99 said:**
> only remove the metapackage and you will be free to uninstall all the eyecandy stuff you dont like/needI &#8222;complain&#8220; not about surplus of packages and about &#8222;eycandy stuff&#8220;. I want to have working desktop... :)
I know, it will be manageable, as it was all this time, it was just a (kind of) unsuccessful sarcasm... Not so easy to get me discouraged...

---

### Post by hugmenot on 2011-04-05
> **sgage said:**
> The Gnome Project has already stated that the panels will continue to be available for the Gnome 3 stack. So officially, The Gnome Project will offer a choice of Gnome Shell or Panels with Gnome 3.

Not really, they already neutered it because they want it to serve as a fallback and hence it has to look and behave like the top strip in Gnome Shell.

I want to be able to keep my minimal setup working, including the look and the applets.

---

### Post by alexcckll on 2011-04-05
As an end-user of Lucid, who bought his Thinkpad R61i and Ideapad S12 preinstalled from Linux Emporium - will the next LTS Major OS Releases (like the move from Hardy to Lucid) ebe certified on my machines?  Or will I have to bin them and buy new computers to run the new Ubuntu systems?

NVIDIA ION chipsets - will they be supported fully in the next LTS? What about Intel X3100? Or will i have to send the machines back as this "Unity" thing will break them so much that I can't boot them?

---

### Post by cariboo on 2011-04-05
@alexcckll, if you are having problems, I'd suggest you start a new thread, instead of tacking on a question on an existing thread

---

### Post by KegHead on 2011-04-05
Hi!

I won't be able to survive w/o Gnome/classic.

KegHead

---

### Post by cecilpierce on 2011-04-05
> **KegHead said:**
> Hi!

I won't be able to survive w/o Gnome/classic.

KegHead

Me 2 neither, whats our next choice ?

:(

---

### Post by cariboo on 2011-04-05
When gnome-panels cease to exist, you have so many other choices, it would probably take a couple of years for you to try them all.

---

### Post by zika on 2011-04-05
I gave a try to Unity-2D today... I can live with it...
Unity-3D is, simply, other story...

---

### Post by beew on 2011-04-05
> **alexcckll said:**
> 
NVIDIA ION chipsets - will they be supported fully in the next LTS? What about Intel X3100? Or will i have to send the machines back as this "Unity" thing will break them so much that I can't boot them?

Kind of off topic, but this is out of the hands of Ubuntu or Linux really. The ION can be "supported" in that there are compatible Linux drivers but in fact you still wouldn't be able to use it. 

The Nvidia chips would be worse than useless for Linux  on laptops with Optimus enabled. So if most Nvidia laptops are going to come with Optimus enabled Nvidia effectively pulls the plug on Linux laptop support. See this thread
[URL="http://ubuntuforums.org/showthread.php?t=1718637"]http://ubuntuforums.org/showthread.php?t=1718637

[/URL]

---

### Post by kansasnoob on 2011-04-05
> **cariboo907 said:**
> When gnome-panels cease to exist, you have so many other choices, it would probably take a couple of years for you to try them all.

Well we don't even know if or when they'll totally cease to exist. We know from what SABDFL is saying that there will be no easily available option to switch to the old panel DE in Oneiric. We don't know how hard it will be obtain that effect and we probably won't know for a few months :)

I did try to describe some potential options in post #10, but I can assure you that SABDFL is NO dummy! If he sees Ubuntu truly losing pace to something like Mint or Fedora we'll see something offered to fill the gap.

I hope by this fall I'll be able to spend more time with Lubuntu. I'd really like to see it move to mainstream Ubuntu support. IMHO it's the latest and greatest shining star of the *buntu community :D

---

### Post by cariboo on 2011-04-05
> **kansasnoob said:**
> Well we don't even know if or when they'll totally cease to exist. We know from what SABDFL is saying that there will be no easily available option to switch to the old panel DE in Oneiric. We don't know how hard it will be obtain that effect and we probably won't know for a few months :)

I did try to describe some potential options in post #10, but I can assure you that SABDFL is NO dummy! If he sees Ubuntu truly losing pace to something like Mint or Fedora we'll see something offered to fill the gap.

I hope by this fall I'll be able to spend more time with Lubuntu. I'd really like to see it move to mainstream Ubuntu support. IMHO it's the latest and greatest shining star of the *buntu community :D

I personally haven't tried it yet, but apparently the gnome-panels in gnome 3 are a pale reflection of their former self, in that they don't have the same functionality as they do in gnome 2. 

Whether they stay around or not has nothing to do with what anyone wants. Gnome seems to be determined to do what they want with out paying attention to anyone else. Ubuntu is a Gnome base distribution, so it can only use what is available to them. I don't think Canonical has the resources to fork out the panels, and keep them compatible with Gnome 3.

---

### Post by webme on 2011-04-05
> **cecilpierce said:**
> Me 2 neither, whats our next choice ?

:(

Anyway, in Oneiric (probably) we would be able to move the position of the launcher as we wish and other features will come, so the launcher will act like GNOME 2.x panel (to support almost everything). The developers will, mainly, focus on Unity and its panel&dock, meaning the GNOME 2.X panel will eventually loose its functionality (most part of it), so, it will be irrelevant.

---

### Post by msrinath80 on 2011-04-05
> **cariboo907 said:**
> I personally haven't tried it yet, but apparently the gnome-panels in gnome 3 are a pale reflection of their former self, in that they don't have the same functionality as they do in gnome 2. 

Whether they stay around or not has nothing to do with what anyone wants. Gnome seems to be determined to do what they want with out paying attention to anyone else. Ubuntu is a Gnome base distribution, so it can only use what is available to them. I don't think Canonical has the resources to fork out the panels, and keep them compatible with Gnome 3.

And why is it not logical to merely pick GNOME 2 and keep maintaining it instead? Isn't it stable and usable after more than a decade of development?? Look at XFCE, they do releases too. But they don't change desktop paradigms ever so radically.  I'd be happy for once if they (GNOME devs and Canonical) truthfully accepted that all they're doing is making it harder for the existing user-base by restricting choices and reverting to unproductive environments. Yes, I know I have choice and all that. The reason for my frustration is simply that I cared a lot for the GNOME desktop; and was quite passionate about it. I  now hate to see it go downhill. When all you have is a hammer, everything looks like a nail to you. Basically, these guys are good (and exceptionally skilled) at coding environments for a desktop experience. This is all fine and dandy. After having refined the desktop experience, they reach the top of the mountain. Now, they don't quite know what to do, and so we're headed downhill. If only Canonical and/or these GNOME devs would care to spend more time working with video drivers or even the Linux kernel instead of ruining the most optimal desktop experience we've had in a long time :(

---

### Post by beameup on 2011-04-05
> **cariboo907 said:**
> When gnome-panels cease to exist, you have so many other choices, it would probably take a couple of years for you to try them all.

Where's my "Like" button??? :)

---

### Post by cariboo on 2011-04-06
> **msrinath80 said:**
> And why is it not logical to merely pick GNOME 2 and keep maintaining it instead? Isn't it stable and usable after more than a decade of development?? Look at XFCE, they do releases too. But they don't change desktop paradigms ever so radically.  I'd be happy for once if they (GNOME devs and Canonical) truthfully accepted that all they're doing is making it harder for the existing user-base by restricting choices and reverting to unproductive environments. Yes, I know I have choice and all that. The reason for my frustration is simply that I cared a lot for the GNOME desktop; and was quite passionate about it. I  now hate to see it go downhill. When all you have is a hammer, everything looks like a nail to you. Basically, these guys are good (and exceptionally skilled) at coding environments for a desktop experience. This is all fine and dandy. After having refined the desktop experience, they reach the top of the mountain. Now, they don't quite know what to do, and so we're headed downhill. If only Canonical and/or these GNOME devs would care to spend more time working with video drivers or even the Linux kernel instead of ruining the most optimal desktop experience we've had in a long time :(

Ubuntu has been, and always will be a Gnome based distribution, Gnome is moving to GTK3, and Ubuntu will too. As of now the two panel interface will not be updated to work with the new libraries. this may change, but I wouldn't hold my breath. From what I understand, there are things that the GTK2 libraries can't do, so new libraries are being created so that that we can benefit from these new capabilities.

Keep in mind that Gnome 3 and Natty haven't even been released yet, with time the customizing capabilities will come back, look at Ubuntu Tweak for instance, for those that didn't like the button change, it allows users to change the buttons back with a couple of mouse clicks. The option to change the buttons wasn't available the day Lucid came out, but the capability was there fairly soon after. I'd say give it some time, by the time the LTS release comes out, we'll probably be wondering what all the complaining was about.

As for the idea that the developers should work on drivers or the kernel, this has been brought up many times before, I don't don't know if you any developers, but of the few I've met, they mostly pick one area to work in, and there isn't much crossover in to other areas. Basically they'd all have to stop what they are doing, and concentrate on learning a new and different type of programming than they have been doing for most of their careers.

---

### Post by manzdagratiano on 2011-04-06
On that note, I would like to add this... around just about every release (both right before and after) - and I have been noticing this ever since Karmic, having started with Jaunty - that every new release superficially seems to be flawed and underwhelming to a large majority of people, and time and again there is the same cycle of posts on the forum, as history may easily corroborate (for instance, the threads "Share with the community your <X> install and upgrade experiences"), that the new release was quite horrendous and the one before was the supreme elixir in computing... and yet, this title of the elixir shifts on the new one in a few months, and before the next release, it is this that is hailed as such, with the new one again regarded as a perversion of all previous releases. Such was easily the case with Lucid, and then with Maverick, and now public opinion has completely reverted...

All I believe this does prove is, that Ubuntu + 1 has ***without fail*** been consistently better than Ubuntu, and unless a new release proves to be otherwise after a couple of months' worth of being out there for the masses, I would beg to disagree with any who say Natty will be any lesser than Maverick. I would only beseech everybody to change their perspective, and try the new offering without prior bias... Change is inevitable, and is not necessarily ever bad... else Ubuntu would never have stemmed out of Debian in the first place and not be here where it is... GNU/Linux itself would not be where it is today

---

### Post by kansasnoob on 2011-04-10
This really scared me so I began to look for alternatives. I think I did a fairly good job of summing what I knew about gnome3 and the ability to revert to a panel setup here:

[http://ubuntuforums.org/showpost.php?p=10652828&postcount=20](http://ubuntuforums.org/showpost.php?p=10652828&postcount=20)

So I joined the project discussed here:

[http://ubuntuforums.org/showthread.php?t=1724486](http://ubuntuforums.org/showthread.php?t=1724486)

Particularly look at post #73. Things are already coming together quickly, and I'm just waiting for an update that should fix a problem or two.

And I've already figured out how to forcibly revert to the fallback mode :D

In "/usr/share/gnome-session/sessions" you'll find a file named "gnome.session". **Please create a backup before trying this with gnome3!** But the second to last line looks like:

```
IsRunnableHelper=/usr/lib/gnome-session/gnome-session-check-accelerated
```

Simply change it to:

```
IsRunnableHelper=/bin/false
```

Also there is a GUI to do this but it doesn't work yet.

Anyway, if Canonical decides to make it nearly impossible to run the classic gnome "look" with gnome3, there will be a way. It might be messy.

I honestly don't understand either Gnome or Canonical going for the "one size fits all" approach.

In general Linux is just NOT a "one size fits all" type of community :D

---

### Post by pony-tail on 2011-04-11
> Anyway, if Canonical decides to make it nearly impossible to run the classic gnome "look" with gnome3, there will be a way. It might be messy.

I honestly don't understand either Gnome or Canonical going for the "one size fits all" approach.

In general Linux is just NOT a "one size fits all" type of community 
"Messy" I can live with !
Unity - I will not

---

### Post by smallblackanimal on 2011-04-18
5 pages of worrying for no reason. If you want the 2 panel GTK 2.3 with support just run 10.04. Its supported till like the year 3000 or so. If you want the cutting edge newest release on your apple II, your going to have to deal with a 2d unity of find the ppa that someone will develop in the future to support the feel that you want. Its 7 months away. Test Natty, make sure its stable, worry about 11.10 when the code is available. Unity has come a long way already (10.10 remix sucked). 7 months of updates and it will probably have a completely different interface anyways and we'll have all new things to complain about :P

---

### Post by treasonvoice on 2011-04-19
I personally don't mind the switch. Things change. Look at that other major yet capitalist OS. It changed. It got rubbish. Then it was developed a bit more and now people are happier with it.

However, the difference between that other unmentionable and ubuntu is that ubuntu is all about customization. So if they want to implement Unity to the exclusion of Gnome-shell/panel, then they can at least allow us to change the way it looks etc. I'm aware, however, that they still need to perfect the basics before letting anyone fiddle with it. And that's fine. Remember. It's still in development and by the time we get to Oneiric it should be at a level where it stops being less than consistent.

Happy, positive, smiley thoughts.

---

### Post by aljazek on 2011-04-19
I am currently using ubuntu 10.10 and I love it. Changes are not so bad from 10.10 -> 11.04, but natty still has a few bugs (mine problem is with older ATI and dash, because I can't see applications till I cross them with cursor). I'll wait for ubuntu 11.10 or switch to xubuntu if it still won't work.

---

### Post by tubunu on 2011-04-26
> **smallblackanimal said:**
> If you want the 2 panel GTK 2.3 with support just run 10.04. Its supported till like the year 3000 or so. 

You mean, two more years, until April 2013, right? :D

---

### Post by KStorm on 2011-04-26
This project is somewhat interesting.

[http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)

---

### Post by kansasnoob on 2011-04-26
Why is this still even being talked about?

While gnome3 is far from stable I've already figured out how to get the forced fall-back to panels.

So the only default offerings will be unity and unity-2d. So what?

How many of us use everything default out-of-box?

---

### Post by Harry33 on 2011-04-27
> **kansasnoob said:**
> Why is this still even being talked about?

While gnome3 is far from stable I've already figured out how to get the forced fall-back to panels.

So the only default offerings will be unity and unity-2d. So what?

How many of us use everything default out-of-box?

Yea, may be so for us experienced users.
But,
Gnome3 will not be there for default setup, not even possible to install it from official repos.
You can have it only from one or two PPA's ATM.
And neither of those work well out of the box. There are issues you know.
The question is, will they ever work perfectly or very well?
This is because main packages in Ubuntu are configured and patched for Unity.

---

