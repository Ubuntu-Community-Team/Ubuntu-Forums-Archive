---
title: "[SOLVED] a good program to burn cds/dvds in ubuntu/feisty fawn?"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by leah1984 on 2008-03-25
hello,im a noob to ubuntu/linux and the computer i have was givin to me but i do not know if it has a dvd burner in it ,so i thought id just give it a try to find out,my question is  what program can i install to try this ,as i am used to using deepburner for windows xp. and i m not sure what is compatible with this operating system? thank you for any help:confused:

---

### Post by BennBuntu on 2008-03-25
I use k3b. It's made for KDE but works fine in gnome. It's a bit like nero for windows. Otherwise gnomebaker is almost the same but made for gnome.


either search in synaptic, the package manager, or type one of the following in a terminal
```
sudo apt-get install k3b
```

or

```
sudo apt-get install gnomebaker
```

happy burning

---

### Post by leah1984 on 2008-03-25
thank you , i found gnomebaker thanks alot

---

### Post by Sweet Spot on 2008-03-25
Don't bother with Gnomebaker, with no offense to the suggestion up above. I was using it for a bit, but realized that when archiving my CD's, or making audio CD's from FLAC files, it would leave gaps in between the songs, which can break the flow of a lot of albums. 

I installed K3b which is for KDE, but runs just the same for Gnome (which I'm running), and is a better idea than looking for "the" perfect Gnome app, which is a waste of time. 

In terms of DVD burning, same advice as before: Don't waste your time with pretty much ANY Linux app. They're all hit and miss, and in my experience, not worth the trouble. Just install WINE, and use DVD Shrink. And for a backup, should DVD Shrink not work because of a scratched or extra encryption scheme, download DVD Fab, and use that under WINE as well. I've been using DVD Shrink since the start, and have attempted to try native DVD burning apps for Ubuntu, but none could come close to being as efficient or easy as it. 

Seriously, do yourself a favor, and avoid the headaches.. Get WINE, DVD Shrink, DVD Fab and K3b for audio. You'll thank me for it. 

Doug.

---

### Post by BennBuntu on 2008-03-25
Native alternative to DVD shrink is k9copy. It's not quite as intuitive, but I've had good luck with it. If the discs are encrypted, you'll need extra codecs you can get from [http://medibuntu.org/](http://medibuntu.org/) and installing ubuntu-restricted-extras

---

### Post by Sweet Spot on 2008-03-25
K9 was a nightmare for me. And others have had a hard time with it as well. Like I've said, it can be hit or miss, but I don't think there's much sense in going with something that isn't sure to work. Wine and DVD Shrink are tried and true, and DVD Fab for a backup, is the best solution IMO.

---

