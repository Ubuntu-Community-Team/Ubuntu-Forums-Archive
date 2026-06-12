---
title: "SiS SI7012 without surround"
date: 2006-01-26
forum: Multimedia &amp; Video
---

### Post by Thunk on 2006-01-26
I have an onboard realtek sound card that plays surround sound wonderfully on XP using AC97. In Ubuntu it'd only use the front speakers and the sub. Any ideas?

Thanks!

EDIT: 

Solved, cheers!

---

### Post by ernz on 2006-10-30
How did you fix this? I have the same sound card with the same problem.

---

### Post by dannyboy79 on 2006-10-30
you guys are lucky!!! My sound was working in Ubuntu to begin with and then all of a sudden it stopped working out of the right speaker and I didn't even mess with alsamixer or anything like that, I simply played some songs in xmms and controlled xmms thru remote desktop using my laptop from the basement. Now I can't for the life of me get the sound to come out of the right speaker even though the speakers work fine in winbloz xp??? Any thoughts????? I have posted this issue in like 3 other threads but NO ONE has offered to help me ONCE!!! Despite the fast that I go around reading threads and if I think I know the answer or think that I can help I open the thread and post my 2 cents to help a fellow Ubuntu user. I have only been on linux since like March. I consider myself past the newbie stage and maybe now a novice. Can you help please?

---

### Post by ernz on 2006-10-30
Hi DannyBoy79! This is probably a stupid question, but is XMMS audio balance centralised and not all the way to one side. Please see image.

[IMG]http://www.aspideas.co.uk/ernz/xmms.png[/IMG]

---

### Post by dannyboy79 on 2006-10-30
i''ll check when I get home but I have played music using other media players and the music still only was coming out of the left speaker but hopefully that's it because you have no idea how irritated I have been. I mean, I built a computer and wish I would have read about supported hardware first because I went with a foxconn motherboard which had the sis mirage graphics built in and it was horrible so I had to upgrade to e geforce 6200 and I would hate to have to buy a sound card now also!!! thanks, and i'll let ya know.

---

### Post by bunnythebunny on 2006-11-24
I am in exactly the same situation as the OP. And i've pretty much got the same hardware (My motherboard is an Asrock, but it shares the same onboard sound card)

i tried this site. to no avail.
[http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml) 

](*,) help. :(

---

### Post by dannyboy79 on 2007-03-08
this is sooooo funny!!! i recently bought a new motherboard anfd cpu and gave my bro the old one, he ended up having the same issue with his speaker only working out of the left side, it turned out that a jumper was missing on the motherboard ac97 audio header. once I connected 2 of the pins, sound came out of both side. it must have appeared to work in winbloz but that must have only been winbloz being able to duplicate the left channel automatically cause that's the side that worked and spit it out the right side. that is very weird that winbloz was able to do that on the fly without me even having to do this. I know i didn't do anythign personally within windows to make it duplicate the left side sound out of the right speaker,  it must be the way it was by default. at least now I know it wasn't ubuntu's fault but my own. i do recall playing with the header cause I was trying to get the front audio panel to work with my headphones and I ended up giving up because my speakers have a jack on them which I just would use.. that's when I myst not have pout back the jumper on the audio header.

---

