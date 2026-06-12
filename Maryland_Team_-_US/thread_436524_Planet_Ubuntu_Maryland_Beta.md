---
title: "Planet Ubuntu Maryland *Beta*"
date: 2007-05-07
forum: Maryland Team - US
---

### Post by ChuckFrain on 2007-05-07
Yes, we have a beta site. After seeing the thread about starting a planet up in the PA fourms,  I decided to try my hand at one myself. 

So point your browser over to [Planet Ubuntu Maryland]("http://planet.ubuntu-maryland.org") and give me some constructive feedback. Currently my and Jono's blogs are on there and once I get done tweaking Jono's will be gone.

Also check out the [wiki page]("https://wiki.ubuntu.com/MarylandTeam/MDPlanetGuideLines") for guidelines on getting your blog added to the aggregation. Read over the page and let me know your thoughts.

Chuck Frain

---

### Post by Iokua on 2007-05-08
It looks pretty good, Chuck. You might want to resize that Ubuntu image so that it displays properly, and if you plan on using hackergotchis, be sure to leave a column open to the left. Can this aggregate any blog with an RSS feed? I noticed Planet Ubuntu mentions that an SSH key is required (for what?) Thanks for the hard work!

---

### Post by ChuckFrain on 2007-05-09
Thanks for the comments. The image will be worked on in the coming days. If you know how to leave the column that you speak of, I'll be glad for the advice. It'll save me time from figuring it out:) (And if any GIMPers want to work on the pic, I won't be offended)

And yes, any RSS, ATOM, and RDF feed can be added to the site. The SSH key is required on the Ubuntu site so that the users can log in themselves and edit the file or run a script to add themselves to the feed. I haven't taken it to that level yet so for now it's a matter of emailing me the[ relevent info]("https://wiki.ubuntu.com/MarylandTeam/MDPlanetGuideLines") and I'll add you manually.

---

### Post by Iokua on 2007-05-09
> **ChuckFrain said:**
> Thanks for the comments. The image will be worked on in the coming days. If you know how to leave the column that you speak of, I'll be glad for the advice. It'll save me time from figuring it out:)

It depends on how you're handling the design. If you're using a CSS-based layout, you just need to add a new floating div to the left of the other two columns. So it'd be something like this:

#left-column {
width: 150px;
float: left;
}

#center-column {
width: 500px;
}

#right-column {
width: 150px;
float: right;
}

If more than one div is aligned to the same position (such as "left") then the floats will stack from left to right, in the order that you call them. This is an extremely basic example though and it'll likely require some tinkering to get it to work properly. You'll likely have to work with padding and margins, and you may want to make the sizes relative rather than absolute. If you run into any trouble, just let me know. I'd be glad to help out.

> And yes, any RSS, ATOM, and RDF feed can be added to the site. The SSH key is required on the Ubuntu site so that the users can log in themselves and edit the file or run a script to add themselves to the feed. I haven't taken it to that level yet so for now it's a matter of emailing me the[ relevent info]("https://wiki.ubuntu.com/MarylandTeam/MDPlanetGuideLines") and I'll add you manually.

Cool. I don't have a blog at the moment but I was considering starting one, so I'll definitely send you the info if I decide to do so.

---

### Post by ChuckFrain on 2007-05-09
That's a great example Iokua. If you want, the template that I used, and is currently unmodified, freely availible at [http://www.ubuntu-uk.org/planet/templatefiles/](http://www.ubuntu-uk.org/planet/templatefiles/) and the file is called planet.css. My CSS skills are limited and with limited time if you could whip something up that would be great.

---

### Post by Iokua on 2007-05-10
> **ChuckFrain said:**
> That's a great example Iokua. If you want, the template that I used, and is currently unmodified, freely availible at [http://www.ubuntu-uk.org/planet/templatefiles/](http://www.ubuntu-uk.org/planet/templatefiles/) and the file is called planet.css. My CSS skills are limited and with limited time if you could whip something up that would be great.

Sure, I'll have some time this weekend, so I'll take a look at it then.

---

