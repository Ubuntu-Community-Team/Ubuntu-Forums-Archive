---
title: "ATI Radeon HD4770 crashing system"
date: 2010-01-22
forum: Multimedia Software
---

### Post by osarusan on 2010-01-22
I'm using Ubuntu 9.10x64, Athlon II x4, 4 gigs of ram, ATI Radeon HD 4770 with fglrx drivers (downloaded from the ATI website and installed as per the Ubuntu community wiki).

I did a clean install of Ubuntu when I put in the ATI card.

I've been having a lot of problems with my system locking up entirely due to video problems. The mouse won't work, ctrl-f1 or f2 don't do anything, no keyboard commands work, in fact, except for doing alt+prscr+REISUB in order to restart.

At first this was happening seemingly at random whenever I watched videos. In another thread, I was able to narrow this down to Compiz, and I solved it by completely removing Compiz. It very rarely happens while watching video files or DVDs now (though it has happened).

In General, 3D gaming seems to work working fine with wine. I can play WoW and Civ4 with no lockups. However, Left4Dead always locks up the system the moment the map loads.

This has also happened with OpenArena.

I'm not so concerned about Wine apps (and I know this isn't the place to ask about them). What I'm concerned about is why this is locking up my entire system rather than, say, just crashing the game.

Can anyone help me figure out why video seems to be taking down my entire system?

---

### Post by user1397 on 2010-01-23
I know this isn't much help, but certain video games and high-quality videos are just designed to work with microsoft software/technology such as directx and the .net framework, and so some videos just take up more resources even though your system is fast.

---

### Post by osarusan on 2010-01-23
True, but I would expect the game to perform poorly or crash in that case, not take down my whole system. Not to mention the fact that I ran the same apps flawlessly before on my older nVidia card. So I'm 99% positive it's due to the fglrx drivers or my newer ATI card.

Again, if I can't play a game, that's too bad, but not so worrying to me. I am worried, however, when my system locks up entirely... That's the problem I'm most interested in solving.

---

### Post by osarusan on 2010-01-29
I found some hints relating to this problem here: [http://forum.compiz.org/viewtopic.php?f=114&t=6794](http://forum.compiz.org/viewtopic.php?f=114&t=6794)

As this problems happens more often for me if I use Compiz (such as when I watch video), I look at the Compiz forums and saw that it may have something to do with PAT. However, it seems like there's some trouble disabling the kernel's PAT in Ubuntu -- the OP from that thread uses OpenSuse, and all the folks using Ubuntu (like myself) were not able to fix the problem by adding nopat to the grub startup line. For me, there's no change at all. The system still freezes up with running some 3d games, and the system locks up when I watch video while Compiz is enabled.

---

### Post by kuric on 2010-12-01
I was experiencing a lot of crashes on a ACER lapton with an ATI Radeon graphic card.

Try to disable **Hyper Threading** technology in BIOS, if you have that option.

---

