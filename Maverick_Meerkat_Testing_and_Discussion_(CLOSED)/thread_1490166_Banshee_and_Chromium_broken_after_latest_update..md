---
title: "Banshee and Chromium broken after latest update."
date: 2010-05-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-05-21
Banshee crashes as soon as i start it with following error.
> [Info  20:36:28.952] Running Banshee 1.6.0: [Ubuntu lucid (development branch) (linux-gnu, i486) @ 2010-04-04 14:18:33 UTC]
[Info  20:36:31.375] All services are started 1.746942s

Gdk-ERROR **: The program 'Banshee' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 3547 error_code 8 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
aborting...
Trace/breakpoint trap


And flash player is broken in chromium. As soon as i open any website it says the plugin has crashed.

Thanks.

---

### Post by go7Ul1ai on 2010-05-21
You're running a development version of Lucid? 

Anyway, Banshee is running fine for me on fully updated Maverick, I'm running Banshee 1.7.0

---

### Post by donniezazen on 2010-05-21
> **lee.jarratt said:**
> You're running a development version of Lucid? 

Anyway, Banshee is running fine for me on fully updated Maverick, I'm running Banshee 1.7.0

Hmmm i upgraded it to maverick by changing lucid to maverick in source list.

---

### Post by DougieFresh4U on 2010-05-21
> **soham_1207 said:**
>  As soon as i open any website it says the plugin has crashed.



I have gotten that messege tonite as well running Maverick.
I am not complaining, just thought rather odd some one else has the same issue

---

### Post by TerminX on 2010-05-22
Downgrade libgtk2.0-0 to 2.20.0-0ubuntu4, 2.21.0-1ubuntu2 is broken.

---

### Post by ronacc on 2010-05-22
this update did break banshee and the flash plugin on my amd64 sys with the 64bit libflashplayer.so  it is saying it isn't even there ( it is, I looked to make sure it hadn't been uninstalled) checked with chroumium , epiphany and Opera , I know opera was finding it and using it prior to this update , now it doesn't even show up as being there . There are reports in another thread that this update broke alot of things .I ran banshee just before the update and it played fine , after the update I get the same as the OP .

---

### Post by jppr on 2010-05-22
> **terminx said:**
> downgrade libgtk2.0-0 to 2.20.0-0ubuntu4, 2.21.0-1ubuntu2 is broken.

+ 1

---

### Post by ronacc on 2010-05-22
if I try to downgrade  libgtk2.0-0 to 2.20.0-0ubuntu4 it wants to take out half my system .

---

### Post by jppr on 2010-05-22
i did that update last night, i use proposed updates and updates comes mainserver. i don´t have any problem update those packages

---

### Post by Amaranth on 2010-05-22
The new GTK+ package enables client-side decorations and RGBA by default. The RGBA by default part causes apps that embed another window to crash. Thus banshee and flash, among others.

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521)

---

### Post by donniezazen on 2010-05-22
> **ronacc said:**
> if I try to downgrade  libgtk2.0-0 to 2.20.0-0ubuntu4 it wants to take out half my system .

Same here.

---

### Post by Amaranth on 2010-05-22
You need to downgrade all of the pieces at once. [https://edge.launchpad.net/ubuntu/+source/gtk+2.0/2.20.0-0ubuntu4](https://edge.launchpad.net/ubuntu/+source/gtk+2.0/2.20.0-0ubuntu4) shows all of the binary packages built from the gtk+ source package. You need to downgrade all of these at once (if you have them installed, that is).

---

### Post by TerminX on 2010-05-22
The powerpuff speaks truth. ;)  You must downgrade all related packages in order to satisfy dependencies.  You can probably safely just do *sudo dpkg -i /var/cache/apt/archives/*2.20.0-0ubuntu4*deb* in order to downgrade all relevant packages at once.

---

### Post by donniezazen on 2010-05-22
> **TerminX said:**
> The powerpuff speaks truth. ;)  You must downgrade all related packages in order to satisfy dependencies.  You can probably safely just do *sudo dpkg -i /var/cache/apt/archives/*2.20.0-0ubuntu4*deb* in order to downgrade all relevant packages at once.

I get following error.


sudo dpkg -i /var/cache/apt/archives/*2.20.0-0ubuntu4*deb
[sudo] password for donnie: 
dpkg: error processing /var/cache/apt/archives/*2.20.0-0ubuntu4*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/*2.20.0-0ubuntu4*deb


Thanks.

---

### Post by zika on 2010-05-22
Is there a way we could, just, switch RGBA off?

---

### Post by zika on 2010-05-22
> **soham_1207 said:**
> I get following error.


sudo dpkg -i /var/cache/apt/archives/*2.20.0-0ubuntu4*deb
[sudo] password for donnie: 
dpkg: error processing /var/cache/apt/archives/*2.20.0-0ubuntu4*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/*2.20.0-0ubuntu4*deb


Thanks.That is because You (like I do) opted not to keep installed packages in archive...

---

### Post by MacUntu on 2010-05-22
I just downgraded to libgtk2.0-0_2.21.0-1ubuntu1_i386 and that was sufficient to stop programs go haywire.

---

### Post by gnomeuser on 2010-05-22
I really like how this was rolled out, in Lucid we had a ppa and we knew that it broke pretty much the universe to enable it. In Maverick with nothing changed at all in this respect.. it's thrown in without any warning or announcement and predictably... it broke frikkin' everything.

Totem, Banshee, aMSN all broke, I haven't dared restart Chromium out of fear that we make it 4 out of 4 of my most used applications.

Planning people.. planning. It is a development release, you are allowed to break stuff, that doesn't mean you should knowingly roll out a change that breaks stuff for which you have:

1) No announcement.
2) No assigned bug task or developers to handle issues being communicated to testers.
3) No change from the last time in terms of the last time this was tried.. in other words utterly failing to learn from our experience.

The roll out in Lucid was much more responsible in comparison. This needs to be reverted and reconsidered immediately and the developer in question (seb128 no less, he should know better) should be put on probation from committing directly to the repo till he learns not to intentionally break the cosmos without prior announcement. I don't care, you just don't do that.. 

It harms Ubuntu, it harms our access to testing (to gain testers after all, one would need to keep a bare minimum of stability). The gain to Ubuntu from doing it this way is exactly zero.

It's so wrong it's not even right.

---

### Post by SevenMachines on 2010-05-22
looks like the flash plugin (i imagine other media plugins too) wont work in chromium but at least it doesnt suffer from the fit inducing problems of firefox at the moment. if anyone hasnt downgraded and is having totem crash on startup problems too, try
$GDK_NATIVE_WINDOWS=true totem
as a temporary workaround

---

### Post by plun on 2010-05-22
Another option is to run this command.

```
export GTK_RGBA_APPS=allbut:firefox:firefox-3.5:gksudo:ooffice:soffice:inkscape:gksu:gtk-recordMyDesktop:kompozer-bin:gpaint:lernid:totem:truecrypt:thunderbird-bin:thunderbird:checkgmail:gloobus-preview:exe:firefox-bin:swiftfox-bin:gnome-mplayer:gnome-screensaver:google-chrome:chromium-browser:prism-bin:gnome-mplayer:xsane:metacity:mutter:firefox-3.7:flashplugin-nonfree

```

Just to add apps to the list, flash doesn't work, unsure about command name :confused:

This can also be within the file .profiles

---

### Post by Longinus00 on 2010-05-22
> **gnomeuser said:**
> I really like how this was rolled out, in Lucid we had a ppa and we knew that it broke pretty much the universe to enable it. In Maverick with nothing changed at all in this respect.. it's thrown in without any warning or announcement and predictably... it broke frikkin' everything.

Totem, Banshee, aMSN all broke, I haven't dared restart Chromium out of fear that we make it 4 out of 4 of my most used applications.

Planning people.. planning. It is a development release, you are allowed to break stuff, that doesn't mean you should knowingly roll out a change that breaks stuff for which you have:

1) No announcement.
2) No assigned bug task or developers to handle issues being communicated to testers.
3) No change from the last time in terms of the last time this was tried.. in other words utterly failing to learn from our experience.

The roll out in Lucid was much more responsible in comparison. This needs to be reverted and reconsidered immediately and the developer in question (seb128 no less, he should know better) should be put on probation from committing directly to the repo till he learns not to intentionally break the cosmos without prior announcement. I don't care, you just don't do that.. 

It harms Ubuntu, it harms our access to testing (to gain testers after all, one would need to keep a bare minimum of stability). The gain to Ubuntu from doing it this way is exactly zero.

It's so wrong it's not even right.

This is pretty ridiculous. Pre-alpha software is typically meant for developers only. Who cares what users think of a version of software that's not even going to make it into the final? Maybe users will wise up and use the normal release until the alpha/beta rolls around.

---

### Post by zika on 2010-05-22
Just for this occasion:
Using Chromuim with flash-block... :)

Still, I miss flash in many occasions... :)
Waiting for a patch...

---

### Post by gnomeuser on 2010-05-22
> **Longinus00 said:**
> This is pretty ridiculous. Pre-alpha software is typically meant for developers only. Who cares what users think of a version of software that's not even going to make it into the final? Maybe users will wise up and use the normal release until the alpha/beta rolls around.

How is it ridiculous to expect that when you know you will interrupt testing that you at least give testers a heads up?

We tested the _exact_ same patch during the Lucid cycle and determined that it broke everything and then some. Even then it was an opt in PPA, it was announced with a call for testing and a tracking bug report.

Now.. nothing, nothing at all, unless you count the massive breakage.

I used to this kind of work for Fedora and not sending out a headups notice when any change affects anything outside the package in question was considered reason for being at least reprimanded. I've done QA within Open Source for years and nowhere is this behavior accepted. It's also counter productive in encouraging testing.

When you know something is going to break you do not remain silent, and trust me in this case we had abundant forewarning of massive breakage.

---

### Post by ronacc on 2010-05-22
> **Longinus00 said:**
> This is pretty ridiculous. Pre-alpha software is typically meant for developers only. Who cares what users think of a version of software that's not even going to make it into the final? Maybe users will wise up and use the normal release until the alpha/beta rolls around.

I stand with gnomeuser on this one . He didn't say USERS he said TESTERS we who are here right from the star are a different breed from normal users and might be considered an auxiliary arm of the developers . He also didn't say don't do it , he said a little warning would be nice when massive destruction is EXPECTED to happen .

---

### Post by plun on 2010-05-22
Well.... we are guinea pigs and are threated as pigs....:P

Perhaps someone can ask Mr Bacher if this is Ok  ? or maybe he dislike RGBA ?

Really bad IMHO....

---

### Post by gnomeuser on 2010-05-22
> **ronacc said:**
> I stand with gnomeuser on this one . He didn't say USERS he said TESTERS we who are here right from the star are a different breed from normal users and might be considered an auxiliary arm of the developers . He also didn't say don't do it , he said a little warning would be nice when massive destruction is EXPECTED to happen .

Here is how such changes must be rolled out.

1) First publish a PPA with the change (since we know it to be extremely destructive)
2) Setup a tracking bug for all issues relating to the feature
3) Allocate developers to handle these bugs
4) Issue a call for testing

Once we tested this for and fixed every application in the default install plus every popular application. Then and only the do you write up the heads up that the change is going to be merged and issue the update.

None of that happened in this case.

Why is merging it directly a bad idea? 

Firstly we know with empirical certainty that it pretty much fscks up the universe, eats babies and other unmentionable matters involving kittens, crayons and C4. We know this because not just a few months ago we tested this very feature using the above mentioned procedure and concluded that we could not fix everything in time for release. 

When we know something is going to be greatly disruptive to testing this means that the selfishness of one developer in doing a direct merge removes testers from pretty much every other aspect of the distro. E.g. how can I test totem when it now frikkin crashes on launch. I can't, that is testing not being done for, days, weeks, who knows months not spent productively ensuring that Maverick is as solid as it can be.

Another really annoying thing about this move is that it was issued on a Friday meaning we now face being entirely frikkin broken till at least Monday when the developers return to work. 

My own options now are limited pretty much to forcing a downgrade and ensuring that the packages do not get updated till the patch is reverted or everything is fixed, second option involves backing down to Lucid. Both are a bother and remain undesirable.

Was this a PPA reverting the breakage and keeping it off my system is a simple ppa-purge away. No such simple mechanism exists when the patch is merged into the master repos. Instead I now have to trawl through and ensure I downgraded every required package by hand correctly.

*edit*

To give people an idea of the potential costs of doing this I did a bit of quick math. 

At 35$/h for software testing (the only rate I was able to find), a weekend of not being able to do testing yields a loss of 12-24 hours of testing for me meaning 420-840$ worth of free work seb128s merge cost Canonical. At that rate to have cost Canonical a million USD in free testing, assuming the lowest numbers some 2380 testers disabled is required. Now 2380 testers of Maverick presently doesn't sound like much of a stretch to me however I don't have the numbers of active testers so I have no way of being sure. This also assumes that Monday morning the issue is resolved either by removing enough bugs to make Maverick testable or reverting the patch. Neither seems likely to happen.

Just saying.

---

### Post by gnomeuser on 2010-05-22
There we are, please mark this sucker up

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/584228](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/584228)

---

### Post by autocrosser on 2010-05-22
> **gnomeuser said:**
> There we are, please mark this sucker up

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/584228](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/584228)

Done my friend.  I'm on the road right now & away from my Testing unit---so this one didn't hit me, but the timing on something like that COULD NOT BE WORSE & it "should" have been rolled out on a Monday at least..........

---

### Post by Slug71 on 2010-05-22
> **gnomeuser said:**
> There we are, please mark this sucker up

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/584228](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/584228)

Confirmed.

---

### Post by dagrump on 2010-05-22
I marked it as affecting me too. That only made six of us though.

---

### Post by taavikko on 2010-05-22
> **jppr said:**
> i did that update last night, i use proposed updates and updates comes mainserver. i don´t have any problem update those packages

Proposed repos **isn't in use with development version**
They are "enabled" after official release...


In topic, doesn't seem to affect my setup...
nvidia's binary blob...

---

### Post by Slug71 on 2010-05-22
No but really, we should ONLY be testing stuff that will make it into the final for that particular release. There shouldnt even be a threads in this forum as a call for testing on something which isnt going to make it(Gnome Shell). A lot of wasted time and distraction. Of course with exceptions to some stuff like apps.
Set up another forum under development and programming called Future Development and Programming or +1 Development and Programming or something so stuff like that can be placed in there. Since we continually get the builds of the latest kernel now and there are PPAs of all kinds for testing, it is quite possible to have a 'rolling development release'.

I think as stated before, there needs to be some level of stability here so that we can remain productive. A heads-up would be nice with a possible revert set to go if needed. If there isnt going to be a separate PPA for stuff like this.

Again this dependency hell needs to be sorted out too. Half of your system shouldnt need to be removed to revert a package. The goes for stuff like evince too. If i wanted to remove it i shouldnt have to be told half my system is going to go with it. Bare minimum only please.

---

### Post by Amaranth on 2010-05-22
This work is going to be in the final release of Maverick. That's why it was uploaded now.

---

### Post by gnomeuser on 2010-05-22
> **Amaranth said:**
> This work is going to be in the final release of Maverick. That's what it was uploaded now.

Don't care, still should be done responsibly.

---

### Post by jppr on 2010-05-22
gtk problem here now is a weird thing. i installed from ppa the daily-build chromium, and this doesn´t have that window border problem in any application. when i close chromium and open firefox the problem is immediately...

---

### Post by ronacc on 2010-05-22
I added my affects me too and a note about the problem about trying to revert . I'm not having the window border/crashing at least on the stuff I have tried but many things arent working right even though they don't crash  ,I'm using the nvidia binary and compiz+emerald .

---

### Post by castrojo on 2010-05-22
> **gnomeuser said:**
> Here is how such changes must be rolled out.

1) First publish a PPA with the change (since we know it to be extremely destructive)

Is there data being lost? Your desktop is unusable, which sucks, but isn't the end of the world for a pre alpha.

> 
Once we tested this for and fixed every application in the default install plus every popular application. Then and only the do you write up the heads up that the change is going to be merged and issue the update.

This isn't the way running Ubuntu+1 works.

> Firstly we know with empirical certainty that it pretty much fscks up the universe, eats babies and other unmentionable matters involving kittens, crayons and C4. We know this because not just a few months ago we tested this very feature using the above mentioned procedure and concluded that we could not fix everything in time for release.

You're overreacting.

> E.g. how can I test totem when it now frikkin crashes on launch. I can't, that is testing not being done for, days, weeks, who knows months not spent productively ensuring that Maverick is as solid as it can be.

It's pre-alpha 1 and early in the GNOME release cycle, we're in feature development mode not testing mode.

> My own options now are limited pretty much to forcing a downgrade and ensuring that the packages do not get updated till the patch is reverted or everything is fixed, second option involves backing down to Lucid. Both are a bother and remain undesirable.

Par for the course at this point in the cycle.

---

### Post by Slug71 on 2010-05-22
> **Amaranth said:**
> This work is going to be in the final release of Maverick. That's why it was uploaded now.

Well had we had the 'other' development and programming forum, we would have been more clear on the status of this. Or with a revert in place in the case of this issue, we wouldnt be stuck with it like now. Or a separate PPA with a call for testing...

Since my window covers my taskbar i cannot do nothing without closing the window i have open. And since you cannot copy and paste text after closing Firefox, this is a real PITA. Cant copy/paste code to terminal with FF open. Cant minimize or maximize it either. Its about time that damn bug gets solved too.
Even Windows with its crap IE doesnt have this problem. 
Show desktop button doesnt work either.

---

### Post by Slug71 on 2010-05-22
> **whiprush said:**
> 
It's pre-alpha 1 and early in the GNOME release cycle, we're in feature development mode not testing mode.



Well testers are still needed to raise the issues whether they were known or not. 
Its a PITA period and regressions like this is careless IMO.

---

### Post by jppr on 2010-05-22
> **Slug71 said:**
> 

Since my window covers my taskbar i cannot do nothing without closing the window i have open. And since you cannot copy and paste text after closing Firefox, this is a real PITA. Cant copy/paste code to terminal with FF open. Cant minimize or maximize it either. Its about time that damn bug gets solved too.
Even Windows with its crap IE doesnt have this problem. 
Show desktop button doesnt work either.

i have just same when i close chromium and start firefox. i run system nouveau-driver and system is amd 64. install now nvidia-current and test system with it.

---

### Post by castrojo on 2010-05-22
> **Slug71 said:**
> Well testers are still needed to raise the issues whether they were known or not. 
Its a PITA period and regressions like this is careless IMO.

You're right! It is careless, luckily you knew that before you upgraded to Maverick!

---

### Post by ronacc on 2010-05-22
I think all of us here in the dev forum understand that breakage is a normal part of testing . Where the problem arises is that to spring MASSIVE breakage on us with no warning and without providing a way out is both thoughtless and unecessary , as pointed out by gnomeuser there is a tried and tested method (special ppa ) to handle this sort of thing .

---

### Post by Slug71 on 2010-05-22
> **whiprush said:**
> You're right! It is careless, luckily you knew that before you upgraded to Maverick!

Yes i did.
A revert in place or maybe waiting till Monday would have been nice though.

---

### Post by gnomeuser on 2010-05-22
> **whiprush said:**
> Is there data being lost? Your desktop is unusable, which sucks, but isn't the end of the world for a pre alpha.


You should really be nicer to your testers you know.. We do man years of work for absolutely free, I would love to see you replace us, given your attitude and mindset you surely will have to.

> 
This isn't the way running Ubuntu+1 works.


Funny you mention it, it sure was during the Lucid cycle.. I can even dig up the mailing list posts and bug reports for you if you need your memory refreshed.

That also isn't in any way an argument against doing things the right way.

> 
You're overreacting.


I doubt that I am, no warning, no information at all, just pretty much every single application broken. Sure I didn't lose any data.. yet, but equally worrying I'm unable to use my data which is a requirement to losing it in the first place. I would argue that is pretty much the same thing. It may be there but it's just as useless to me as if it wasn't.

Given the experience in the Lucid cycle with this feature, I doubt I will be seeing my data any time soon regardless. 

> 
It's pre-alpha 1 and early in the GNOME release cycle, we're in feature development mode not testing mode.


The patch has not progressed since it was tested for Lucid. You knew this would happen and you didn't even warn anyone. In this specific case you had every bit of knowledge that you would **** up the universe by merging the feature now. Considering that was what happened the last time and all. I remember because I actually volunteered my setup to test this for you back then.

We, your testers, I am sure are all very grateful for your honesty and frankness in dismissing our willingness to help you, free of charge. You just tell us when we are welcome in your community project.

---

### Post by zekopeko on 2010-05-22
Could you all stop pointing fingers and try and fix this?

@devs

Make note of this sort of behavior and implement mechanism to eliminate this sort of uber breakage in the future.

---

### Post by castrojo on 2010-05-22
> **gnomeuser said:**
> You should really be nicer to your testers you know.. We do man years of work for absolutely free, I would love to see you replace us, given your attitude and mindset you surely will have to.



This hasn't got anything to do with being nice or not, it has to do with things that churn at any given point in the cycle. At what point wasn't I being nice?

> The patch has not progressed since it was tested for Lucid. You knew this would happen and you didn't even warn anyone. In this specific case you had every bit of knowledge that you would **** up the universe by merging the feature now. Considering that was what happened the last time and all. I remember because I actually volunteered my setup to test this for you back then.

I had no idea any of this would happen.

> We, your testers, I am sure are all very grateful for your honesty and frankness in dismissing our willingness to help you, free of charge. You just tell us when we are welcome in your community project.

I am not dismissing your willingness to help. I'm just wondering why you think that a prealpha is going to work at this point in the cycle. Most of the platform team aren't even running Maverick at this point, which is probably why it wasn't tested on real hardware yet.

You seem to be under the assumption that someone specifically decided to break everyone's applications on purpose. I think you want a big banner that says "Warning GTK is going to break today" when you totally drove by the sign that said "This is prealpha and will eat babies." 5 miles ago and didn't pay attention to that sign either.

---

### Post by zekopeko on 2010-05-22
> **whiprush said:**
> This hasn't got anything to do with being nice or not, it has to do with things that churn at any given point in the cycle. At what point wasn't I being nice?

I had no idea any of this would happen.

I am not dismissing your willingness to help. I'm just wondering why you think that a prealpha is going to work at this point in the cycle. Most of the platform team aren't even running Maverick at this point, which is probably why it wasn't tested on real hardware yet.

You seem to be under the assumption that someone specifically decided to break everyone's applications on purpose. I think you want a big banner that says "Warning GTK is going to break today" when you totally drove by the sign that said "This is prealpha and will eat babies." 5 miles ago and didn't pay attention to that sign either.

The point is that who ever pushed this had enough information from Lucid to know this isn't going to be a walk through the park.

The timing was awful no matter how pre-alpha this is. Nobody is going to bitch about a single app breaking because of a bad upload, but this is a system wide change. It shouldn't have been treated as any other update.

What gnomeuser suggested is how things should have been done for something this big.

---

### Post by fluteflute on 2010-05-22
Maverick isn't even at Alpha stages yet, it will eat your babies, that's why we don't use it for anything even vaguely important yet. 

As I understand it we haven't even been asked to test it yet, it's to early on and things are too unstable. 

This hasn't made systems unbootable or impossible to update or killed hardware: we should consider ourselves lucky.

---

### Post by donniezazen on 2010-05-22
> **gnomeuser said:**
> I really like how this was rolled out, in Lucid we had a ppa and we knew that it broke pretty much the universe to enable it. In Maverick with nothing changed at all in this respect.. it's thrown in without any warning or announcement and predictably... it broke frikkin' everything.

Totem, Banshee, aMSN all broke, I haven't dared restart Chromium out of fear that we make it 4 out of 4 of my most used applications.

Planning people.. planning. It is a development release, you are allowed to break stuff, that doesn't mean you should knowingly roll out a change that breaks stuff for which you have:

1) No announcement.
2) No assigned bug task or developers to handle issues being communicated to testers.
3) No change from the last time in terms of the last time this was tried.. in other words utterly failing to learn from our experience.

The roll out in Lucid was much more responsible in comparison. This needs to be reverted and reconsidered immediately and the developer in question (seb128 no less, he should know better) should be put on probation from committing directly to the repo till he learns not to intentionally break the cosmos without prior announcement. I don't care, you just don't do that.. 

It harms Ubuntu, it harms our access to testing (to gain testers after all, one would need to keep a bare minimum of stability). The gain to Ubuntu from doing it this way is exactly zero.

It's so wrong it's not even right.

+1 Sums up all. I really like @ubuntustatus on twitter which used to warn about faulty upgrades but i am not sure if it is still active.

---

### Post by ranch hand on 2010-05-22
> **gnomeuser said:**
> There we are, please mark this sucker up

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/584228](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/584228)
Done that.

---

### Post by ranch hand on 2010-05-22
> **whiprush said:**
> You're right! It is careless, luckily you knew that before you upgraded to Maverick!
Yup sure did.

---

### Post by ranch hand on 2010-05-22
> **fluteflute said:**
> Maverick isn't even at Alpha stages yet, it will eat your babies, that's why we don't use it for anything even vaguely important yet. 

As I understand it we haven't even been asked to test it yet, it's to early on and things are too unstable. 

This hasn't made systems unbootable or impossible to update or killed hardware: we should consider ourselves lucky.
Oh come now, I think babies are probably no more than made ill.  Kittens though are probably goners.

---

### Post by ranch hand on 2010-05-22
> **Longinus00 said:**
> This is pretty ridiculous. Pre-alpha software is typically meant for developers only. Who cares what users think of a version of software that's not even going to make it into the final? Maybe users will wise up and use the normal release until the alpha/beta rolls around.
I am not sure what you are getting at.

This is put out there so that it can be tested.  It is not made easy because otherwise you would panic the unwashed hordes that start coming in on the Alphas.

It is going to be real tough to get folks to test the ISO for A1 if they do not already use the OS and know what it is up to.

This is supposed to make it to the final, read the blue print.

---

### Post by MacUntu on 2010-05-22
What's all the fuzz about? A warning would have been nice, didn't happen. System stays bootable and a simple downgrade will temporarily fix it. Case solved. :KS

---

### Post by SevenMachines on 2010-05-22
> **MacUntu said:**
> What's all the fuzz about? A warning would have been nice, didn't happen. System stays bootable and a simple downgrade will temporarily fix it. Case solved. :KS

Ditto, I was about to mention exactly the same points but less eloquently :) A warning would be nice but its a painless downgrade/upgrade for testing switch. Reaching a working desktop with a couple of applications having problems is a blessing compared to sitting staring at a busybox prompt wondering what to try out next:)

---

### Post by Longinus00 on 2010-05-22
> **ronacc said:**
> I stand with gnomeuser on this one . He didn't say USERS he said TESTERS we who are here right from the star are a different breed from normal users and might be considered an auxiliary arm of the developers . He also didn't say don't do it , he said a little warning would be nice when massive destruction is EXPECTED to happen .

What is it exactly you're testing? None of the packages you have installed now are going into the final version so how are you helping? Developers don't really care if the system breaks now because in a sense they are trying to break it by testing new things out. At no time do I remember any guarantee about system stability during this stage. If you can't work past these problems yourself (downgrading, writing a patch, etc.) this is not the time to be installing a development release. Stick with testing in a vm or something.

---

### Post by ranch hand on 2010-05-22
Lets see, two new kernels so far.  Seems like the apps in it need tested against those kernels, at the least.

We have just 9 days to ISO testing.  It would be nice if there were no big surprises therein.

I have no problem with breakage anywhere in the testing cycle either.

I have not reverted my system.  I am running, right now, on 10.10 fully updated.  I do have to run desktop effects on "normal" rather than "none".  I do not like that but we are testing and know (should anyway) that this is not a normal OS.

The complaints, I think, are somewhat reasonable.  I do not think that it is worth the effort as it could be a lot worse.

Your objection to testing at  this point even makes a little sense but not a lot.  There is no need for a lot of testers at this point.  There is a need for some testers for 2 reasons.

1>upcoming ISO testing.  This should be important to you if you are planning on getting in at A1.  If you are not, why are you here wasting your time?
2>most of the devs should still be on 10.04 working on bugs there, not wasting time looking for bugs here.  We can do that, why should they?  I do not expect this to have a fast fix but I bet it is not there for A1.  Call me on that one if I am wrong.

---

### Post by ronacc on 2010-05-22
all we are asking for is a little warning when particularly massive breakage is expected , I for one would have probably proceded to update anyway , I have a standalone testbox dedicated to testing and totaly isolated from my work system so the worst that can possibly happen would be a reinstall , which I expect to do many times during the dev cycle anyway (testing milestones and dailies ).I don't think that a "lookout You are about to step in deep poo poo" would be a terrible burden on the devs .

---

### Post by Slug71 on 2010-05-22
> **Longinus00 said:**
> What is it exactly you're testing? None of the packages you have installed now are going into the final version so how are you helping? Developers don't really care if the system breaks now because in a sense they are trying to break it by testing new things out. At no time do I remember any guarantee about system stability during this stage. If you can't work past these problems yourself (downgrading, writing a patch, etc.) this is not the time to be installing a development release. Stick with testing in a vm or something.

Yes the package which broke the system being discussed here IS making it to final. They are not trying to break it either. Breakage happens, sometimes knowingly.

---

### Post by Slug71 on 2010-05-22
Anyway, not the end of the world. Its known and is probably being worked on.

You do, do a great job Devs. and we really do appreciate what you do!

---

### Post by xeizo on 2010-05-23
I'm new here but agree "it's not the end of the world", even though I necessarily don't have any opinion on how things should be done. I leave that to those who are initiated. 

Maverick is possibly surprisingly stable at the moment, but as I understand it's because it hasn't been fully turned into a real Maverick yet. It's still mostly Lucid with some newer packages. 

I expect things to break galore sooner or later.

Lucid had the most stable development cycle I've ever experience in Linux, mabe because it was destined to be a LTS-release, no heavy experimentation was going on.

I've been using Linux since Red Hat 5.0, and have used all the larger distros from time to time. Earlier on I used to appreciate Mandrivas Cooker for being unusually usable during development, but Lucid turned out to be more stable all the time than Cooker ever has been. Or any other distro I've experienced during development.

Now, if Maverick is to introduce some cool new paradigms and features, as I see it things have to be broken more than the last time. A lot more. 

Devs, you have my full support to do the new thingies all the way :)
If we wan't stable, 10.04 is the way to go. Maverick will possibly be less stable than 10.04 even in it's final shape. It's not LTS.

About what broke this time; I run a fully updated Maverick with some extra ppa:s like Ricotz unstable. I also noticed that xsane crashed helplessly, conky became only partly functional and fonts got blurry in Wine but are ok on the desktop itself. 3D-Games run just fine. Other than that, I didn't notice anything particular. I run Compiz with extras on, gnome-desktop and gnome do in docky mode with Nvidia 256.25. 

The box is still essentially "stable", it's up 24/7 running my playing-around-with website(xeizo.com)  ;)

---

### Post by jppr on 2010-05-23
I have  just installed the nvidia-current driver and the problem disappeared  gtk, window-border problem isn´t anymore in any particular application. Problem was with nouveau-driver.

Edit. Nouveau-driver was that window-border problem only when open and use Firefox, with PPA daily-build Chromium it wasn´t. = )

---

### Post by zika on 2010-05-23
> **jppr said:**
> I have  just installed the nvidia-current driver and the problem disappeared  gtk, window-border problem isn´t anymore in any particular application. Problem was with nouveau-driver.

Edit. Nouveau-driver was that window-border problem only when open and use Firefox, with PPA daily-build Chromium it wasn´t. = )ATI here... Problem is still acute...

---

### Post by mejy on 2010-05-23
> **gnomeuser said:**
> I really like how this was rolled out, in Lucid we had a ppa and we knew that it broke pretty much the universe to enable it. In Maverick with nothing changed at all in this respect.. it's thrown in without any warning or announcement and predictably... it broke frikkin' everything.

Totem, Banshee, aMSN all broke, I haven't dared restart Chromium out of fear that we make it 4 out of 4 of my most used applications.

Planning people.. planning. It is a development release, you are allowed to break stuff, that doesn't mean you should knowingly roll out a change that breaks stuff for which you have:

1) No announcement.
2) No assigned bug task or developers to handle issues being communicated to testers.
3) No change from the last time in terms of the last time this was tried.. in other words utterly failing to learn from our experience.

The roll out in Lucid was much more responsible in comparison. This needs to be reverted and reconsidered immediately and the developer in question (seb128 no less, he should know better) should be put on probation from committing directly to the repo till he learns not to intentionally break the cosmos without prior announcement. I don't care, you just don't do that.. 

It harms Ubuntu, it harms our access to testing (to gain testers after all, one would need to keep a bare minimum of stability). The gain to Ubuntu from doing it this way is exactly zero.

It's so wrong it's not even right.

If Maverick had reached beta or even had a single pre-release made then I would agree, but we're currently 10 days before even the first alpha release.  They've made no request for testers - it's quite evident that if there's a radical change as has been made it will have consequences, and information from testers is of no use until you've sorted out underlying issues that you know exist.  Once they're out the way, input on unexpected bugs becomes useful.

On past releases dpkg, xorg and other crucial packages have been broken at this time because it's not *meant to be working*.

If your list of requirements were followed throughout the development process, things would move slower, there would be added overhead and nothing of benefit would be achieved.

---

### Post by zika on 2010-05-23
Just to make it clear. I consider this as self-inflicted wound... :)

---

### Post by xeizo on 2010-05-23
Kjell L. has fixed the bug;

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/584228](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/584228)

link to download in the thread, for those who can't wait for official packages ...

---

### Post by LKjell on 2010-05-23
Anyone has a screenshot of this beautiful breakage? I am using xmonad and there is no title bar to break. Windicator seems to be a cool feature that need this client side decoration.

---

### Post by gnomeuser on 2010-05-23
> **LKjell said:**
> Anyone has a screenshot of this beautiful breakage? I am using xmonad and there is no title bar to break. Windicator seems to be a cool feature that need this client side decoration.

There is nothing to see yet, outside that is nothing working which doesn't screenshot well.

While csd was the inspiration for windicators it isn't apparently doing to be part of the implementation.

[http://www.markshuttleworth.com/archives/333#comment-327213](http://www.markshuttleworth.com/archives/333#comment-327213)

There also appears to be some considerable problems with csd as an approach considering it isn't cross toolkit.

[http://blog.martin-graesslin.com/blog/2010/05/why-you-should-not-use-client-side-window-decorations/](http://blog.martin-graesslin.com/blog/2010/05/why-you-should-not-use-client-side-window-decorations/)

All in all I am currently not even seeing any justification for why we need this. Granted I didn't attend UDS so maybe justification has been provided there as well as some idea of why we need it.

So in terms of published information, there is very little to justify merging it now given that it breaks pretty much all the desktop.

What are we going to use it for, I know that rgba support is required for some of the things the design team have been talking about, or at least it could open up for some interesting improvements.. but csd?

---

### Post by LKjell on 2010-05-23
Just need to trust the developers to do some sane work and do not invent the wheel twice.

Well I will keep a keen eye on client side decoration in the change log.

---

### Post by zika on 2010-05-24
It seems that we will not get a quick fix. Instead, I see that Totem is getting fixed not to crash with current csd. What about Flash plugin? It seems that FF (3.7) has gone step toward solving the situation, but, not completely. Chromium is, still, Flash free...

---

### Post by Slug71 on 2010-05-24
Installed XFCE desktop and problem solved. :P

---

### Post by gnomeuser on 2010-05-24
> **zika said:**
> It seems that we will not get a quick fix. Instead, I see that Totem is getting fixed not to crash with current csd. What about Flash plugin? It seems that FF (3.7) has gone step toward solving the situation, but, not completely. Chromium is, still, Flash free...

Since it appears that the patches will not be reverted and tested in a PPA. I think it is up to seb128 and the other developers who will be fixing this mess to guide us to how they would prefer us to inform them on the extend of the breakage.

The last time we had a tracker style bug. In bugzilla I think the correct approach would be to create a metabug then file bugs against each application known to be broken and set those to block the metabug. I don't think Launchpad supports a similar workflow so it is really up to them to write some documentation on how we go about this.

So far I've seen totem, banshee, amsn break at least.

---

### Post by donniezazen on 2010-05-24
> **MacUntu said:**
> What's all the fuzz about? A warning would have been nice, didn't happen. System stays bootable and a simple downgrade will temporarily fix it. Case solved. :KS

Sir, Can you please help me downgrade the packages?

---

### Post by xeizo on 2010-05-24
It's been said already, use these instead if you trust them:  [http://folk.uio.no/kjele/gtk/](http://folk.uio.no/kjele/gtk/)  it's exactly the same versions, so there is no problems replacing with them. Use the Deb-installer and confirm to install anyway, when it protests you should use packages from the channel instead. After that, you have to blacklist the original versions, otherwise these bug fixed ones will be replaced back to the "bad ones" when you update the next time.  Hopefully this is only a temporary evil :)

---

### Post by donniezazen on 2010-05-24
> **xeizo said:**
> It's been said already, use these instead if you trust them:  [http://folk.uio.no/kjele/gtk/](http://folk.uio.no/kjele/gtk/)  it's exactly the same versions, so there is no problems replacing with them. Use the Deb-installer and confirm to install anyway, when it protests you should use packages from the channel instead. After that, you have to blacklist the original versions, otherwise these bug fixed ones will be replaced back to the "bad ones" when you update the next time.  Hopefully this is only a temporary evil :)

Do i have to first remove gtk from the system, then install from the link above and lock version to avoid its upgrade? What exact file do i have to remove/install?

Thanks.

---

### Post by portis on 2010-05-24
> **soham_1207 said:**
> Do i have to first remove gtk from the system, then install from the link above and lock version to avoid its upgrade? What exact file do i have to remove/install?

Thanks.

Try adding my ppa, portis25/ia32libs

---

### Post by donniezazen on 2010-05-24
> **portis said:**
> Try adding my ppa, portis25/ia32libs

Thanks a lot. Fast and easy solution.

---

### Post by zika on 2010-05-25
> **portis said:**
> Try adding my ppa, portis25/ia32libsThere are no descriptions of what is different in Your ppa. There are several packages, beside gtk, that would be upgraded. What is new? Would using Yours gtk put us in a dead-end street regarding to testing or will mainstream override Your version... I have some bad experiences with "patched" packages so I'm cautios...
Anyone tried...? (I need Flash so... I'm sort of desperate... :))
To paraphrase one of the famous movies: Is it safe!?

Update: Is there somebody that has Flash plugin working in Maverick at present ime? I was thinking, if my use of 64-bit pre-release version might, now, produce these problems I have... Anybody with Flash plugin (official) that works out there?

---

### Post by LKjell on 2010-05-25
> **gnomeuser said:**
> Since it appears that the patches will not be reverted and tested in a PPA. I think it is up to seb128 and the other developers who will be fixing this mess to guide us to how they would prefer us to inform them on the extend of the breakage.

The last time we had a tracker style bug. In bugzilla I think the correct approach would be to create a metabug then file bugs against each application known to be broken and set those to block the metabug. I don't think Launchpad supports a similar workflow so it is really up to them to write some documentation on how we go about this.

So far I've seen totem, banshee, amsn break at least.

Totem should work according to the change log. However, I think that the metabug idea is good if the packages are related. As I see now csd just happen to introduce a lot of bugs and assume it get pulled in for Maverick and there happens to be an application that break that has not been tested kinda suck. And we have future applications that have to be patch to get csd to work correctly. Making package maintainer a much harder work. Therefore we can either make csd work with other programs or that other programs work with csd.

---

### Post by erkiha on 2010-05-25
> **Slug71 said:**
> Installed XFCE desktop and problem solved. :P

Somewhat easier workaround is to install openbox and when logging in choose GNOME/openbox session. This way you get almost normal gnome layout and experience, only window decorations are taken care of by openbox.

---

### Post by zika on 2010-05-25
> **erkiha said:**
> Somewhat easier workaround is to install openbox and when logging in choose GNOME/openbox session. This way you get almost normal gnome layout and experience, only window decorations are taken care of by openbox.If You choose OpenBox do You have Flash plugin working? Sorry for being annoying but I need Flash to do some stuff today, and I hate to go to another machine... :) I had terrible experience once upon a time when I installed other window manager in Gnome, so I'm cautious now... :) I, also, do not want to spoil testing experience so...

Update: To answer myself, no, FlashPlugin craches in OpenBox, also...

Question fot Mingming (a.k.a. portis25) : Is FlashPlugin going to be working if I were to choose to use packages from Your ppa...?

---

### Post by portis on 2010-05-25
> **zika said:**
> If You choose OpenBox do You have Flash plugin working? Sorry for being annoying but I need Flash to do some stuff today, and I hate to go to another machine... :) I had terrible experience once upon a time when I installed other window manager in Gnome, so I'm cautious now... :) I, also, do not want to spoil testing experience so...

Update: To answer myself, no, FlashPlugin craches in OpenBox, also...

Question fot Mingming (a.k.a. portis25) : Is FlashPlugin going to be working if I were to choose to use packages from Your ppa...?

Yes, flashplugin works in my 64bit system.
I did nothing, but dropped the csd patch.
Yes, there are other packages in the ppa.
Although I believe that they are harmless to you system, maybe a separate ppa is better.

---

### Post by zika on 2010-05-25
> **portis said:**
> Yes, flashplugin works in my 64bit system.
I did nothing, but dropped the csd patch.
Yes, there are other packages in the ppa.
Although I believe that they are harmless to you system, maybe a separate ppa is better.When I wrote ppa, I meant ports25/ia32libs... Do You mean that ppa by "separate ppa"...?

---

### Post by LKjell on 2010-05-25
Can't you just add the ppa install the packages and then remove the ppa and then pin the packages?

---

### Post by zika on 2010-05-25
Upgraded to (all) stuff from portis25/ia32libs and everything works. Cool! Thank You!

---

### Post by hugmenot on 2010-05-25
Looks like Inkscape has fancy new psychedelic pattern swatches.
Or not?

---

### Post by zika on 2010-05-25
> **erkiha said:**
> Somewhat easier workaround is to install openbox and when logging in choose GNOME/openbox session. This way you get almost normal gnome layout and experience, only window decorations are taken care of by openbox.I was stubborn and I made OpenBox work as I like it. It is very cool and it reminds me of old days... Thank You, very much, for that pointer! It'll be hard to go and try Gnome again... :) 20% increase in graphics (speed) and, even, more in responsiveness... Great advice!

---

### Post by gnomeuser on 2010-05-27
> **LKjell said:**
> Totem should work according to the change log. However, I think that the metabug idea is good if the packages are related. As I see now csd just happen to introduce a lot of bugs and assume it get pulled in for Maverick and there happens to be an application that break that has not been tested kinda suck. And we have future applications that have to be patch to get csd to work correctly. Making package maintainer a much harder work. Therefore we can either make csd work with other programs or that other programs work with csd.

I think I accidently figured out how to do this while filing a papercut bug.

The next papercut bug will be on producing clear easy and automated papercut bugs. That was just way to much work.

However now Seb128 has instructed us in the bug report to open separate bugs against each program.

Do we have steps to confirm that CSD or RGBA are the cause of a crash, such as running it then rerunning with the app excluded?

Then how do we consolidate the bugs, a csd and rgba tag?

Regardless let's get a bughunting, now the fun begins.

---

### Post by gnomeuser on 2010-05-27
Here's the original strong flavor aMSN segfaulting on startup.

[https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/583975](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/583975)

Now questions remains as to how to link this to gtk+.

I plan to write up a testers guide for rbga and csd with instructions on how double check the cause being csd or/and rgba as well as how to file bugs correctly. 

As no information on how this is preferred done and I am definitely uncomfortable with certain aspects of Launchpad which work completely different from what I am used to in Bugzilla expect progress to be a tad slow.

---

### Post by LKjell on 2010-05-27
Just add the gtk-csd tag and let the upstream figure out if it is csd or rgba issue?

---

### Post by donniezazen on 2010-06-06
> **portis said:**
> Try adding my ppa, portis25/ia32libs

I reinstalled the Alpha 1 to see Banshee still has crashing problem. What has happened to this ppa it's no longer active. Any other way to make Banshee work.

Thanks.

---

### Post by SevenMachines on 2010-06-06
[FONT=Arial][COLOR=Black]apps that are currently a little broken due to the client side decorations change might be runnable if you disable rgba, ie[/COLOR][/FONT][FONT=Arial][COLOR=Black][SIZE=2] 
$ XLIB_SKIP_ARGB_VISUALS=1 banshee
should work
[/SIZE][/COLOR][/FONT]

---

### Post by Vanishing on 2010-06-06
> **SevenMachines said:**
> [FONT=Arial][COLOR=Black]apps that are currently a little broken due to the client side decorations change might be runnable if you disable rgba, ie[/COLOR][/FONT][FONT=Arial][COLOR=Black][SIZE=2] 
$ XLIB_SKIP_ARGB_VISUALS=1 banshee
should work
[/SIZE][/COLOR][/FONT]

Thanks a bunch mate.

---

### Post by donniezazen on 2010-06-06
> **SevenMachines said:**
> [FONT=Arial][COLOR=Black]apps that are currently a little broken due to the client side decorations change might be runnable if you disable rgba, ie[/COLOR][/FONT][FONT=Arial][COLOR=Black][SIZE=2] 
$ XLIB_SKIP_ARGB_VISUALS=1 banshee
should work
[/SIZE][/COLOR][/FONT]

Thanks.

---

