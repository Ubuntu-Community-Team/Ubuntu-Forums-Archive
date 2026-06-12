---
title: "Front Audio Not Working"
date: 2012-08-21
forum: Multimedia Software
---

### Post by Eternal Thought on 2012-08-21
Hello everyone.
As the title says, for some reason I can't hear anything when I plug headphones to the front audio.
I thought maybe my hardware is defective since I googled and didn't find anything regarding the same problem with the same motherboard I have, but everything works fine when I boot Windows 7.
In Kubuntu the back panel audio works just fine, even the front record works, just the front audio is problematic.
I tried downloading drivers, checking it's not muted, even upgraded the kernel to 3.5, but it still doesn't work.

My motherboard is Gigabyte GA-Z77-D3H, and the case is Antec P280 (though I'm pretty sure that one is irrelevant to the problem).

Any ideas?

---

### Post by sandyd on 2012-08-21
***Moved to ***[s]***ABT***[/s][I][B] Multimedia & Video
[/B]-sorry about double move
[/I]

---

### Post by miegiel on 2012-08-21
> **Eternal Thought said:**
> Hello everyone.
As the title says, for some reason I can't hear anything when I plug headphones to the front audio.
I thought maybe my hardware is defective since I googled and didn't find anything regarding the same problem with the same motherboard I have, but everything works fine when I boot Windows 7.
In Kubuntu the back panel audio works just fine, even the front record works, just the front audio is problematic.
I tried downloading drivers, checking it's not muted, even upgraded the kernel to 3.5, but it still doesn't work.

My motherboard is Gigabyte GA-Z77-D3H, and the case is Antec P280 (though I'm pretty sure that one is irrelevant to the problem).

Any ideas?
Hi **[COLOR="DarkOrange"]Eternal Thought[/COLOR]**, welcome to ubuntu forums.

Try this: [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
After *Basic troubleshooting* and *Advanced troubleshooting* make sure you check *Further Information* too (if it's not solved already).

Report back if it doesn't help you.

---

### Post by Eternal Thought on 2012-08-22
Sorry for posting in the wrong forum and not replying sooner, it was already nighttime.
Anyway, I followed those guides and it didn't help. Though I'm not sure I followed them correctly, especially the part about installing the new ALSA drivers, I think it may have something to do with the new kernel, but I have no idea.

What else can I do?

---

### Post by miegiel on 2012-08-23
> **Eternal Thought said:**
> Sorry for posting in the wrong forum and not replying sooner, it was already nighttime.
Anyway, I followed those guides and it didn't help. Though I'm not sure I followed them correctly, especially the part about installing the new ALSA drivers, I think it may have something to do with the new kernel, but I have no idea.

What else can I do?

I'm not always that fast with replying either :) and sometimes I wait to see if someone else drops in with useful suggestions. Besides, you do have sound, just not at the output you prefer. So I assume the problem isn't a really big problem.

Regarding "upgrading alsa drivers", when you get to a point where you need to compile stuff, it's time to hit the breaks. Compiling is for the advanced linux users and undoing the process can take more effort than just reinstalling kubuntu. Regrettably guides that tell you to compile something, often omit a warning for people that are new to linux. :(

However, when you checked the [alsa mixer]("https://wiki.ubuntu.com/Audio/Alsamixer"), did you see an output volume lever for both the front and rear or just 1 lever for the rear? For example, on my laptop I have a headphone and a speaker lever. Also make sure you select the proper sound "card" (even though you only have 1 sound card, there might be a virtual device too).

---

### Post by Eternal Thought on 2012-08-26
Tried playing with ALSA mixer a bit now. Tried turning on everything and enabling everything, still had no result, and I did have special bar for the front.
Choosing the appropriate sound card was no good, I only had one option there.

So I guess I just file a bug report or something and hope it's fixed in the next kernel update or something? :(

---

### Post by miegiel on 2012-08-28
> **Eternal Thought said:**
> Tried playing with ALSA mixer a bit now. Tried turning on everything and enabling everything, still had no result, and I did have special bar for the front.
Choosing the appropriate sound card was no good, I only had one option there.

So I guess I just file a bug report or something and hope it's fixed in the next kernel update or something? :(

If (in alsamixer) at the bottom of front sound bar it say "MM" it's muted (when it says "00" it's unmuted), make sure its not.

Is the motherboard you have a new model? It often takes a little longer in linux to get new hardware properly supported. Mostly due to lack of support by the manufacturer. They seem to be afraid their secrets get out if they support people making their hardware work with linux. The result is (I'm generalizing here) that when new hardware arrives in the stores it works in linux, but there are alot of bugs. After 6 months all essential functions work and after a year it should be fully functional. Since supported hardware is is built into the kernel (as modules), a kernel that enables your front audio will arrive one day. Reporting a bug and supporting the person(s) working on the bug (they often don't have the affected hardware) with information and testing fixes can speed things up, but it will still take some time.

Until then, you could extend the rear audio to the front with a cable, or (my favorite) turn the pc around :D

---

### Post by Eternal Thought on 2012-08-28
I tried unmuting everything, but it still didn't work.
And yes, I think it is a fairly new model, so the lack of cooperation is probably the problem.
Anyway, thanks for trying to help. It's not the end of the world since I have the back audio, it's just frustrating that your new hardware has those minor bugs right out of the box, but I'll survive. Especially since Kubuntu is great so far. :)

---

