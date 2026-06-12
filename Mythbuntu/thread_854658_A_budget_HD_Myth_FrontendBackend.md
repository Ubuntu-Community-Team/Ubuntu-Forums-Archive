---
title: "A budget HD Myth Frontend/Backend"
date: 2008-07-09
forum: Mythbuntu
---

### Post by SupremeSpike on 2008-07-09
[http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=12226727](http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=12226727)

I will also be getting at least 1 maybe 2 HD-5500 cards.  This is my first time configuring a Myth box in general so I am not for sure the of limitations of the system.  For example, does 1 card allows a person to either watch or record 1 channel at the sametime?  Would this processor allow the recording of one channel and the viewing of another at the best quality resolution without coming to a crawl?  I also want to be able to stream from my myth box to any of my or my roommates laptops at once.  Would this put too much of a strain on the system if it is streaming to three laptops?

Any help is appreciated!  Have a great day!

---

### Post by klc5555 on 2008-07-10
> **SupremeSpike said:**
> [http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=12226727](http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=12226727)

I will also be getting at least 1 maybe 2 HD-5500 cards.  This is my first time configuring a Myth box in general so I am not for sure the of limitations of the system.  For example, does 1 card allows a person to either watch or record 1 channel at the sametime?  Would this processor allow the recording of one channel and the viewing of another at the best quality resolution without coming to a crawl?  I also want to be able to stream from my myth box to any of my or my roommates laptops at once.  Would this put too much of a strain on the system if it is streaming to three laptops?

Any help is appreciated!  Have a great day!


I use a couple of HD5500s on a Mythbuntu 7.10 machine with Myth 0.20.2. It is a combined master backend and a frontend; I have a Slackware 12.1 box in use as a remote frontend, where, since no 0.20.2 binaries exist for Slack, I compiled all the necessary stuff from source.

The HD5500s each tune one signal at a time. This signal can be watched, recorded, or watched and recorded simultaneously. The signal that each 5500 tunes may be digital or analog. The cards are great at digital incl. HD. The analog component of these cards can be ...frustrating, and if you intend to do much watching/recording of analog signals you may wish to supplement your 5500s with a cheap analog card.

In the Mythbuntu backend, I found that I originally could not use both 5500 cards simultaneously with HD signals in the default Mythbuntu single-disk configuration. Too many read-writes going on simultaneously. After adding a second, fast SATA disk with just the myth recordings directory on it, and bumping RAM up to 1.5 Gigs (on a 3.0 Gig Intel processor with an NVidia7300 card) I have no trouble watching/recording HD from both cards simultaneously.

The remote Slackware frontend has 2 Gigs of RAM, but (at the moment) only a 1.8 Gig AMD processor (a so-called Athlon 2400+, and an NVidia 6200), and while this is perfectly fine for analog and SD watching, it's  not quite fast enough for watching HD content --live or recorded. There's just a barely-perceptible pre-buffering pause every 2-3 seconds that becomes annoying.

So I can't answer your multiple-laptop streaming question, but as for the rest, my opinion is that for 2 of these cards operating full-out, you'll need 2 fast disks and a fairly fast processor on the backend, and each frontend watching needs a very fast processor, with a good NVidia card, and a fast ethernet connection to the backend.

I also use a couple of windows laptops and an XP desktop occasionally to watch things, using Myth player for windows. This is OK for less-than-HD, but HD content seems unsatisfactory.

Cheers!

---

### Post by mrand on 2008-07-10
> **SupremeSpike said:**
> [http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=12226727](http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=12226727)

I will also be getting at least 1 maybe 2 HD-5500 cards.  This is my first time configuring a Myth box in general so I am not for sure the of limitations of the system.  For example, does 1 card allows a person to either watch or record 1 channel at the sametime?  Would this processor allow the recording of one channel and the viewing of another at the best quality resolution without coming to a crawl?  I also want to be able to stream from my myth box to any of my or my roommates laptops at once.  Would this put too much of a strain on the system if it is streaming to three laptops?

Any help is appreciated!  Have a great day!

For the laptop streaming, do you have a wired or wireless network?  Stock 802.11g might not have enough bandwidth, depending on encoding rates - streaming all three on wireless might require either wired or 802.11n wireless.  Stock 802.11g gets < 30 Mbps real-world, which for three young guys from a file server, doesn't seem like enough to me.
 
[INDENT]Marc[/INDENT]

---

