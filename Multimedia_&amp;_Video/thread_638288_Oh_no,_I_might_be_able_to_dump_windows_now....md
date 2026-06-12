---
title: "Oh no, I might be able to dump windows now..."
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by BLTicklemonster on 2007-12-11
Huh. I must be doing something wrong. I have a couple of new dvds I want to copy so the kids won't *FREAKING DESTROY THEM*, and came down here to try to decrypt/rip/burn them, and of course started off in ubuntu to see if I could do it (which I never can seem to do) before booting to windows and doing it there.

So I first off tried to decrypt the first one with dvd decryptor in wine, and it lost audio in the first part of the movie. So on a lark, I tried to use k9copy to make an iso, and work with it later. I set it to make an iso on a spare drive that is accessible to XP, and let it do it's thing. 

Danged if, once done, it didn't up and open k3b like it was wanting to burn the dvd for me. How cute, it thinks it can rip and burn a dvd without decrypting it. No wait, upon further inspection, k3b shows the disk size to be appropriate, and the file structure looks like it is ready to really burn a dvd.

Why not? I removed the dvd, dropped a blank disk in, and let it run. 

Huh. It worked. 

What's up with that, and why in the name of Sam Hill haven't I ever done that before? Did I do something wrong? It can't be that easy, can it? These are pretty new releases. I'm floored. This is going to save me some real money when the kids can leave ripped dvds sitting on the coffee table to spill drinks on and all that fun stuff they do.

So, I might just have a good reason to remove XP from my computer completely. Cool.

---

### Post by CHFFriday on 2007-12-12
I have post on this Form trying to get info on this DVD subject. This has become a big challenge to me.

From what I have read, not only on this form but all over the Internet, Ripping and Burning DVD movies is complicated and success is governed by many factors that Linux programs are not always able to deal with.

 Windows product “AnyDVD” can ALWAYS deal with what ever the Movie Companies through out there for copy protection. I don’t know how they get away with it but they do. I heard it is because it is produced in China.

Anyway I’m much interested in what you have said here. Please provide me with this information.
What Movie Company made the Movie you are talking about?
What date was the DVD made? Not the movie date.
Is the movie DL? 
What where the setting on K9?

BIG THANKS for you help,
CHFFRiday

---

### Post by BLTicklemonster on 2007-12-12
Ripit4me is good, too, for windows. You'll still need dvdshrink and dvd decryptor installed, plus one or two other things listed on the site when you go get ripit4me.

I think this is all baloney. I copy to archive, not sell on the open market. Pirates who sell ripped dvds need to be perse- I mean prosecuted, but leave those of us who are only safeguarding our discs alone.

so anyway, k9copy and k3b are both in the repos, so 

sudo aptitude install k9copy k3b

when you bring up k9copy, you will see where the program wants to burn to a device, change this to an image file ( iso), and chose a place for it to save to.

Now click copy.

Shortly thereafter k3b pops up. At least it did for me. I didn't configure anything, and it did this automatically, and also chose the 4.2 gig size. At which point I dropped a blank disk in and burned.

I'll look things over tonight to see more about it and post back.

Evan Allmighty and Transformers. (second disk of transformers. the first one was very popular, and I hadn't archived it yet, so the studios butt-boinked me twice on that one)

---

### Post by BLTicklemonster on 2007-12-12
Okay, first off, I'm running gutsy, I don't know if that makes a difference.

Start k9copy, go to settings, configure k9copy, and in the left side of the window that pops up, click on dvd, and make sure the disk size is set correctly for your dvd. 4300 is what I have mine set to because I may have a dual layer burner, but I've only got singles. Next, check the boxes that say Burn with k3b, Auto burn, and Quick scan (if you want that one, I've got no idea if it made a difference).

Now you're ready to rip.

Put a dvd in, click file, open, and you should see the file structure of your dvd pop up. You will have to check what you want to have burn.

Look for "Output device" above where it shows the dvd file structure. Set it to ISO image, and chose a place to put the iso.

Now click on Actions, and copy.

What happened for me was it had a progress bar that showed when it was done, then k3b started up, and I swapped disks, and clicked burn in the k3b console. It took less time to do all of this than it takes dvdshrink to finish it's first check of a dvd.

Now I have no idea where the ISO I made went, because the folders I made are empty. I guess I did something wrong along the way, but hey, it worked fine.

Hope this helps, Friday.

---

