---
title: "Mono and Banshee"
date: 2011-01-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Nerd_bloke on 2011-01-07
Slightly hesitant to ask after the last thread I posted in...

Even during Maverick there was a push to remove Mono as a default dependency (Shotwell replacing F-Spot) and Canonical have been pushing hard to justify every MB on the ISO images.

A lot of work had been put into Rhythmbox, why the sudden change of heart towards Banshee?

Do any new packages now depend on Mono; I thought there was only Tomboy left?

---

### Post by Harry33 on 2011-01-07
> **Nerd_bloke said:**
> Slightly hesitant to ask after the last thread I posted in...

Even during Maverick there was a push to remove Mono as a default dependency (Shotwell replacing F-Spot) and Canonical have been pushing hard to justify every MB on the ISO images.

A lot of work had been put into Rhythmbox, why the sudden change of heart towards Banshee?

Do any new packages now depend on Mono; I thought there was only Tomboy left?

At least now yes.
Latest Natty ubuntu-meta package changed ubuntu-desktop.
Now ubuntu-desktop recommends banshee. Rhythmbox was dropped at the same time.

I wonder the same thing. Banshee has caused a lot of problems (extensions especially) in Maverick.
And yes, it takes space in CD.

---

### Post by lidex on 2011-01-07
Yes, my understanding also. I even switched from tomboy to gnote to remove the last dependency - wtf?

---

### Post by Mr. Picklesworth on 2011-01-07
> **Nerd_bloke said:**
> Slightly hesitant to ask after the last thread I posted in...

Even during Maverick there was a push to remove Mono as a default dependency (Shotwell replacing F-Spot) and Canonical have been pushing hard to justify every MB on the ISO images.

A lot of work had been put into Rhythmbox, why the sudden change of heart towards Banshee?

Do any new packages now depend on Mono; I thought there was only Tomboy left?

I think you're misunderstanding the reason for the switch to Shotwell. It was chosen because it has an awesome, active upstream that wants the application to work wonderfully on Ubuntu. And because it already works wonderfully.
Mono doesn't really factor into it. Granted, we don't have many things depending on Mono now, but as long as excellent applications are written with Mono they (and it) will be pulled along.

Feel free to write a Banshee competitor with Vala, though a clone isn't really the same thing since it implies the original will always be the more mature product. And, as mentioned, choosing Banshee is as much about the Banshee community as it is the product. It is a large, healthy, active group of people, enough of whom actively want this thing to shine in Ubuntu and, by extension, to make Ubuntu shine.

---

### Post by Nerd_bloke on 2011-01-07
Still a bit confused TBH; there was initial talk about dropping Rhythmbox for Banshee a few releases back, this stalled when a few issues like gapless playback were still outstanding. 
There was also the Mono issue (mainly about on the space it would save dropping from default installation, being mentioned in lot of the UDS videoed sessions).

The Banshee devs fixed the outstanding list, but Ubuntu stuck with Rhythmbox anyway and put a lot of effort into it working with the new indicator system. Now they are dropping Rhythmbox...

Just wondering how the timeline worked out, seems like it would have made more sense to default to Banshee earlier if it was the long term goal.

---

### Post by castrojo on 2011-01-07
> **Nerd_bloke said:**
> The Banshee devs fixed the outstanding list, but Ubuntu stuck with Rhythmbox anyway and put a lot of effort into it working with the new indicator system. Now they are dropping Rhythmbox...

The soundmenu and indicator work is all player agnostic - it works with any player that uses MPRIS. (It's a little buggy in Banshee/Natty right now but there will be a release next week that will fix that).

---

### Post by sgage on 2011-01-07
I'm not a huge anti-mono guy, but I just prefer Rhythmbox. I've been trying Banshee for a long time, and it always conveys an impression of bloat, and has been quite unstable at times.

Change can be good or bad, but sometimes it seems there's just change going on for the sake of change. The whole Unity thing seems bizarre to me - why put a netbook interface on the desktop?

At least now there are many Ubuntu/Debian derivatives to use, and at least for now you can customize things any which way. Right now I'm playing with PinguyOS, which is interesting...

---

### Post by dino99 on 2011-01-07
my choice goes to : clementine :)

---

### Post by SushiR on 2011-01-07
You can still use the player you like most. There is always a choice. It's just about default applications, and the Ubuntu team decided to use Banshee as default now. Nothing wrong with that, if you ask me. The Banshee team was (and IS) working hard to meet Ubuntu's needs. CPU usage is drastically reduced, so is the memory usage.

I don't know, if I will use Banshee as my default player, but I appreciate the effort to make it a better player.

---

### Post by lidex on 2011-01-07
> **castrojo said:**
> The soundmenu and indicator work is all player agnostic - **it works with any player that uses MPRIS**. (It's a little buggy in Banshee/Natty right now but there will be a release next week that will fix that).

So how do I get it to work with Exaile??

---

### Post by zekopeko on 2011-01-07
> **lidex said:**
> So how do I get it to work with Exaile??

Send a patch to Exaile upstream.

---

### Post by castrojo on 2011-01-07
> **lidex said:**
> So how do I get it to work with Exaile??

This looks like a good place to start: [http://sunng.info/blog/2010/11/exaile-sound-menu-integration/](http://sunng.info/blog/2010/11/exaile-sound-menu-integration/)

---

### Post by lidex on 2011-01-07
> **castrojo said:**
> This looks like a good place to start: [http://sunng.info/blog/2010/11/exaile-sound-menu-integration/](http://sunng.info/blog/2010/11/exaile-sound-menu-integration/)

Thanks for that.

---

### Post by pferraro on 2011-01-08
> **lidex said:**
> So how do I get it to work with Exaile??

[https://bugs.launchpad.net/exaile/+bug/618483](https://bugs.launchpad.net/exaile/+bug/618483)

---

### Post by directhex on 2011-01-08
> **Nerd_bloke said:**
> Slightly hesitant to ask after the last thread I posted in...

Even during Maverick there was a push to remove Mono as a default dependency (Shotwell replacing F-Spot) and Canonical have been pushing hard to justify every MB on the ISO images.

I've never been informed of any push from anyone involved in Ubuntu development to remove Mono. Saving space, definitely, but the space used for Mono apps tends to be much smaller than non-Mono apps, so the space used for the require parts of Mono itself tends to balance out fairly well.

> A lot of work had been put into Rhythmbox, why the sudden change of heart towards Banshee?

Canonical invested some time in integration and extension work for Rhythmbox a cycle or two ago. The same functionality was duplicated into Banshee. I wrote the U1MS addin myself.

> Do any new packages now depend on Mono; I thought there was only Tomboy left?

Tomboy and Gbrainy in Maverick.

---

### Post by Killigrew on 2011-01-09
Ubuntu has to work around some serious bug in Banshee to make Ubuntu 11.04 shine.
Rhythmbox is an awesome Player, its is light, fast, and mostly stable in a way that it never crashed for me.
I tried Banshee in my 10.10 install on 3GHz CPU + 6GB Ram + Vertex 2 SSD,
in 10 min of using, it crashed completely two times.
i could not choose the Folder and File Layout i use for my Music Files as in Rhythmbox and the worst thing, where i don't believe they will ever fix it, is that it is awful slow.
In Rhythmbox you can easily browse you musik collektion without any delay.
Banshee uses this Cover Pictures i don't want and produces lags of ~0,5 sec.
This is absolutly intollerant, it feels like using a 486 and not a new fast computer.
BTW this was the reason i originaly switched from windows to ubuntu.
Now i know i can easily install Rhythmbox but if you are new, your first impression counts
and Banshee doesn't give me one at all. 

greetings :)

---

### Post by directhex on 2011-01-09
> **Killigrew said:**
> Files as in Rhythmbox and the worst thing, where i don't believe they will ever fix it, is that it is awful slow.
In Rhythmbox you can easily browse you musik collektion without any delay.
Banshee uses this Cover Pictures i don't want and produces lags of ~0,5 sec.

Try installing this package to see if it helps: [http://packages.ubuntu.com/natty/libsqlite3-0](http://packages.ubuntu.com/natty/libsqlite3-0)

Yes, that's the 11.04 version of a library, that's the idea.

Some delay is an inevitable price of a difference in how Banshee and Rhythmbox work - RB loads your entire library into RAM, in a fairly wasteful way. Banshee avoids loading your entire library, so needs to do new SQLite lookups whenever you scroll (which costs in CPU time, but keeps RAM use down). The newer SQLite should help, since versions between 3.7.0 and 3.7.2 are completely broken, but it will never be eliminated entirely as long as Banshee uses its magic lookup-based scrolling.

---

### Post by Killigrew on 2011-01-09
hi, thanks for explanation

you where right, with the new library it is fast, but still slower then RB as you said.
So it is because banshee uses the Ram more efficiently, right?
But i have 6GB of Ram that costs nearly nothing in comparison to the rest of the pc..
and funnily, with the same Music Library and no Plugins installed in Banshee
it uses 43MB of Ram where Rhythmbox only uses 37MB!?

Hope they have there Reasons for switching, i still don't like it ...
But Rhythmbox is by far not perfect, so, lets see what we get in April ;) 

greetings :)

---

### Post by amano on 2011-01-09
> **Nerd_bloke said:**
> A lot of work had been put into Rhythmbox,...

Only few people (rather just Jonathan Matthew) work on rhythmbox and they are not really cooperative or at least friendly with feature request, ignoring the needs of the community.

You need proof? Have a closer look at this bug report and make up your own mind: [https://bugzilla.gnome.org/show_bug.cgi?id=582968](https://bugzilla.gnome.org/show_bug.cgi?id=582968)

I am glad that Ubuntu is leaving Jonathan Matthew and Rhythmbox behind. And even if Mr. Schestowitz and friends are right that Mono will be killed, your dogs will all be shot and your toasters melted, Ubuntu should move to just another player instead (Exaile or others).

---

### Post by saulgoode on 2011-01-10
> **amano said:**
> Only few people (rather just Jonathan Matthew) work on rhythmbox...

Odd. The [GIT log]("http://git.gnome.org/browse/rhythmbox/log/") for the Rhythbox project indicates that within the last month there have been commits made by 20 different people -- 19 of whom were not Jonathan Matthew. 

> **amano said:**
> ... and they are not really cooperative or at least friendly with feature request, ignoring the needs of the community.

You need proof? Have a closer look at this bug report and make up your own mind: [https://bugzilla.gnome.org/show_bug.cgi?id=582968](https://bugzilla.gnome.org/show_bug.cgi?id=582968)

Seems like a rather courteous Bugzilla discussion over a proposed feature change, hardly warranting the accusations you've made.

---

### Post by amano on 2011-01-10
> **saulgoode said:**
> Odd. The [GIT log]("http://git.gnome.org/browse/rhythmbox/log/") for the Rhythbox project indicates that within the last month there have been commits made by 20 different people -- 19 of whom were not Jonathan Matthew. 

But most of this "coding pumping army" were just translators who didn't contribute actual code. And most things by "real coders" were just small and easy fixes or fixes to Plugins (Jamendo, Magnatune). Just look at those contributions and get your facts straight.

---

### Post by fluteflute on 2011-01-10
> **amano said:**
> But most of this "coding pumping army" were just translators who didn't contribute actual code. And most things by "real coders" were just small and easy fixes or fixes to Plugins (Jamendo, Magnatune). Just look at those contributions and get your facts straight.
Small and easy fixes, alongside fixes to plugins are very important. Translations also so. It's the little things, the polish that makes the difference. Just because a bug is "small and easy", doesn't mean it makes a huge difference to Rhythmbox users.

---

### Post by SushiR on 2011-01-10
So now it's about who contribute more or better code to a project? Sorry, but can we stick to the topic?

I have no issues with Mono, in fact I couldn't care less about what language it is written in, as long as a player does what I want it to do. I'm not a big fan of Banshee, neither performance wise nor feature wise. It has it's moments, but (for me) is still lacking some stuff other players have already. But the Banshee dev team really puts an efford in making Banshee a better player, and it succeed so far.

There are other audio players, Rhythmbox, Guayadeque, Clementine - to mention a few - but either they are still under HEAVY development (to gain stability and solve usability issues) or the development sort of stalled. Either way, this isn't the best base for a system that is made to appeal new users (and maybe to surprise old ones). So let's be honest, this is the right decision for Ubuntu. And every one's free to install every player he (or she) likes to.

---

### Post by saulgoode on 2011-01-10
> **amano said:**
> But most of this "coding pumping army" were just translators who didn't contribute actual code. And most things by "real coders" were just small and easy fixes or fixes to Plugins (Jamendo, Magnatune). Just look at those contributions and get your facts straight.

"Just looking" at the [Banshee contributions]("http://git.gnome.org/browse/banshee/log/") reveals the same pattern -- the majority of the contributions* made by the Banshee "coding pumping army"** consists of language translations and small fixes.



* The number of total contributions (in a given time period) to the two projects are basically equivalent.

** Banshee's commits, over the last month, are attributable to 24 different contributors opposed to Rhythmbox's 20.

---

### Post by amano on 2011-01-10
*Sigh*

The difference between those numbers is the difference in real code contributors. Both are translated into the same languages, thus the numbers of translators are similar. One translator for each language.

If Jonathan Matthew is the big coder on rhtyhmbox, Aaron Bockover, Alexander Kojevnikov, Bertrand Lorentz, Gabriel Burt and Alex Launi.

---

