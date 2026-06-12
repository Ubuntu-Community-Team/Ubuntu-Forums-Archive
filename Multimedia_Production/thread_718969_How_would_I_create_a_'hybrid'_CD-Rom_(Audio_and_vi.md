---
title: "How would I create a 'hybrid' CD-Rom? (Audio and video etc)"
date: 2008-03-08
forum: Multimedia Production
---

### Post by Tomosaur on 2008-03-08
**I have now discovered K3B's 'Mixed-Mode'. Any help with creating a cross-platform interface is still much appreciated!**

Hello!

I have something of a challenge here. I'm not really sure if it could be done at all, but I would like any pointers any of you might have :)

I want to make a cd which will play in any normal CD player, but which also has data files on such as videos and images. I know this can be done, as I've seen such CDs being used on Windows machines. They're fairly regular I guess. I'm not talking about a simple data cd with mp3 files on, but an actual audio cd like you'd buy in any music shop, but with extras.

Most of the time such CDs auto-run in Windows with a flash interface or something like that. I'm willing to ignore that bit for now, and would just like to know whether I could do such a thing in Linux / Ubuntu, and if so, how?

If I did decide to go with an interface, I would really like to make this cross platform, so if anyone has any tips on that front I'd very much appreciate it. I'd prefer to avoid flash, and would ideally like to use something open-source, but which doesn't require the end user to install anything that they're not likely to have already on their machines. I realise this bit is a bit far fetched, but if anyone has a solution I'd be very grateful.

So, to summarise, I'm trying to:[LIST]
[*]Create an audio CD with extras such as video and images.
[*]Create an inteface which will work on Linux, Windows, and Mac (this is not absolutely necessary, but I think it'd be a nice touch).[/LIST]I don't really care about copy-protection here, in fact it's a bonus if the user is able to simply copy files from the CD using their file-browser.

Sooo, given all this, would I be able to do such a thing in Ubuntu / Linux? All of the tutorials I've seen so far are centered around Windows, using Windows software :S

I do have Windows, but not some of the software I apparently need to use in Windows (and I don't like pirating software :S)

---

### Post by chipants on 2008-03-09
it is possible to create a mixed format cd with linux.

it's super easy in K3B.

if you haven't already installed it, do so:

sudo apt-get install k3b

when you launch K3B, the welcome screen gives a number of options for projects you can create:

New Audio CD Project,
New Data CD Project,
New Data DVD Project,
Copy CD,
Burn CD Image,
Burn DVD ISO Image,
and Further Actions

Click on 'Further Actions', then select 'New Mixed Mode CD Project'.

At that point, you are able to drag and drop files to 'K3B data project' (which can be renamed to whatever you want) or 'Audio Tracks'.

any data you want can go into the data partition, including any windows-style autorun file that you may want to include. any supported audio files can be dropped in the 'Audio Tracks' partition.

then, all  you have to do is burn your disc.

simple as pie. mmm, pie.

---

### Post by Tomosaur on 2008-03-09
Yeah, I discovered the mixed mode in K3b not long after I posted this thread. Sod's Law eh? :P

Thanks for taking the time to help though!

---

