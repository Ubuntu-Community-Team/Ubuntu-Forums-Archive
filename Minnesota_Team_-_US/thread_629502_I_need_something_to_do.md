---
title: "I need something to do"
date: 2007-12-02
forum: Minnesota Team - US
---

### Post by Oompa23 on 2007-12-02
At the moment I have no need to anything special in linux, does anyone have any ideas for a project to keep myself busy and help me learn (im kinda of a noob) I run ubuntu 7.10 gusty gibon but i do have the ISO's downloaded for debain and OpenSuse 10.3 . Any suggestions would be great

---

### Post by yoder on 2007-12-06
Play with VMWare.  Set up a (web, mail, dns, file, --fill in the blank--) server and putz around with the configs.  Put X-Plane on it (my favorite).  Make a media center out of it.

Lots more where that came from.

---

### Post by tonyyarusso on 2007-12-09
Work on upgrading out team's wiki page!  :)
See [https://wiki.ubuntu.com/MinnesotaTeam/Sandbox](https://wiki.ubuntu.com/MinnesotaTeam/Sandbox)

---

### Post by rusty0101 on 2008-04-30
Some people may think this cruel, but that's mostly because it's far more work than the description would suggest.

Run 'apt-cache pkgnames' on both a debian system (against a complete library) and an ubuntu system (with universe and multiverse active) and do a diff between them. You'll very likely come up with a list of a few apps that are in Debian, but not in Ubuntu. Get the src and depends for what looks like an interesting debian package, and work towards building an ubuntu package from them.

For something that won't leave you wanting to beat me over the head for all the frustration that it generates, pick a file in the /usr/bin directory, do a man and info against that file, and see if you can write a better explanation of what the file does, how someone can use it, and give some examples of uses that might not be well known. Include doing searches on Google for how the file is documented elsewhere.

If you are interested in programming, you could do some of the same things with libs that are on your system. How can you call the functions, etc. to make your programming life easier.

Use the apropos command on some key word you're familiar with, and see what commands 'match' to that keyword.

Build a better backup program. I would like to 'backup' just those files that are not automatically created by programs, so no thumbnails, are not part of a distribution package, so pretty much nothing in the /bin /sbin /usr folders. If it's automatically installed by a package, but is currently different from the package file, I want a diff of that file stored in a user archive. And I want all of my e-mail and 'documents' files, well everything in my home directory that isn't automatically created. If the same file exists in 2 locations, but are not 'linked' the backup program may 'link' them to save space, but needs to be able to unlink them when restoring the data. i.e. if they are linked when backup was started they should be linked afterwords. If not, then they shouldn't be. But if you can save space in the backup, and thus time, link them for that purpose.

How about a mp3 player updater. Thinking of the stand alone mp3 player (iPod, zen, nexus, archos, etc.) You plug it in and the updater looks for a 'task' file some place. That tells the updater what parts of the player are off limits to being updated. (Don't touch my ZZTop collection here.) and what types of 'media' are appropriate for this player. (I want the 3 latest podcasts from twit.tv security now, net@night, and the last 2 weeks of the Daily Giz Wiz, and the remaining space should be randomly selected rock, easy listening, and jazz in a 40-20-40 mix, save time by leaving what's in the current mix there if it's going to be in the new mix. No Videos, I can't play Ogg or Aac.) Another player might be audio books only. You could have an e-book reader that you want it to update the reading list from time to time. (though I don't think I'll ever be able to go through all of a 2 gig sd card, fill it? sure, read it? probably not.)

Just some ideas.

---

### Post by camccall on 2008-05-08
Setup OpenVPN or some other VPN software.  At least that's my current project.

---

### Post by ShodanjoDM on 2008-05-08
Download source packages and learn to compile. Or if you like more challenge, download the source packages of the newer version of the programs that's still not available in the official repos.

That will keep you busy for days.

You may be surprised that the applications you compile yourself might seem more responsive. Atleast that's what I found.

---

### Post by krome on 2008-07-02
I have a laptop project - if we can get 15 (older, modem!) laptops to work and find people who need and can use them, we can even get more and distribute them...need to have some progress before Aug. 1 but can have an onging project - we're in Minneapolis.

---

### Post by mplscomputer on 2008-07-16
> **Oompa23 said:**
> At the moment I have no need to anything special in linux, does anyone have any ideas for a project to keep myself busy and help me learn (im kinda of a noob) I run ubuntu 7.10 gusty gibon but i do have the ISO's downloaded for debain and OpenSuse 10.3 . Any suggestions would be great

SOMETHING TO DO: We're running firefox browser on ubuntu and want to customize mouse functions... such as mouse single left click to open url links (not double click) BUT make a mouse single click on image files (jpg, gif, png, tiff) automatically save the image into a specified folder for later viewing.  Stylish or Greasemonkey could probably do it with the right person behind the design wheel... but we don't know have the people who can do it.  We will offer 10,000 share options in our new company for these tasks... not worth much now but we're all working hard to bring the value up in the next couple of years so all of our shares are worth owning.  Interested?

[email]wendy.pareene@gmail.com[/email]  Wendy

---

### Post by trinoquad on 2008-07-21
> **krome said:**
> I have a laptop project - if we can get 15 (older, modem!) laptops to work and find people who need and can use them, we can even get more and distribute them...need to have some progress before Aug. 1 but can have an onging project - we're in Minneapolis.
sounds interesting. It's a great idea but my question is from where are you(team) getting laptops, how! If you could provide some info please...

thanks in advanced
Jrgfjard

---

### Post by binger on 2008-08-18
Spread word about the Pandora! 
[http://openpandora.org/](http://openpandora.org/)

The perfect compliment to your Ubuntu laptop/desktop.  I'm not sure if its being developed yet, but maybe work on a project that is an interface when you plug in the Pandora to your Ubuntu station for transferring/updating music/games/video/etc.

---

