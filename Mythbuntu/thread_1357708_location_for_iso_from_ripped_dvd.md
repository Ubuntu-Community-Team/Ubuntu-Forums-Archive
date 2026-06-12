---
title: "location for iso from ripped dvd"
date: 2009-12-17
forum: Mythbuntu
---

### Post by meanmrmustard on 2009-12-17
I've ripped a dvd using the 'import dvd' function and it appears to have done the job but I cannot find the .iso file.
Where should this file be?
I'm using the Jaunty version of Mythbuntu.

---

### Post by klc5555 on 2009-12-17
> **meanmrmustard said:**
> I've ripped a dvd using the 'import dvd' function and it appears to have done the job but I cannot find the .iso file.
Where should this file be?
I'm using the Jaunty version of Mythbuntu.

default would be /var/lib/mythtv/videos

Use thunar to search for *.iso (*.vob) files if it isn't there. Also if the Myth ripper has some sort of issue with the rip (not always easy to tell from the front end screen), the ripper not infrequently simply deletes the ripped *.iso or *.vob file that it has made, so that there may actually be nothing there at all. Annoying to be sure.

---

### Post by meanmrmustard on 2009-12-17
> **klc5555 said:**
> default would be /var/lib/mythtv/videos

Use thunar to search for *.iso (*.vob) files if it isn't there. Also if the Myth ripper has some sort of issue with the rip (not always easy to tell from the front end screen), the ripper not infrequently simply deletes the ripped *.iso or *.vob file that it has made, so that there may actually be nothing there at all. Annoying to be sure.

That's what I thought.
No .iso file there - guess it failed.
Thanks!

---

### Post by Zeedok on 2009-12-18
> **meanmrmustard said:**
> That's what I thought.
No .iso file there - guess it failed.
Thanks!

I've had trouble with the myth import function before.  I have been using k9Copy to make an .iso, then I save it in the videos folder (as listed above).  Then, go into mythtv  -- utilities/setup -- videomanager and locate your file, search for the metadata on imdb and then the video will be listed in your "Videos"

---

### Post by rhpot1991 on 2009-12-19
There is a bug on this issue: [https://bugs.launchpad.net/mythbuntu/+bug/469583](https://bugs.launchpad.net/mythbuntu/+bug/469583)

Unless you set that directory ripping will fail.  Setting this directory up can also help you with ISO playback, I have done a writeup on this on my site: [http://www.baablogic.net/drupal/node/7](http://www.baablogic.net/drupal/node/7)

---

### Post by klc5555 on 2009-12-20
> **rhpot1991 said:**
> There is a bug on this issue: [https://bugs.launchpad.net/mythbuntu/+bug/469583](https://bugs.launchpad.net/mythbuntu/+bug/469583)

Unless you set that directory ripping will fail.  Setting this directory up can also help you with ISO playback, I have done a writeup on this on my site: [http://www.baablogic.net/drupal/node/7](http://www.baablogic.net/drupal/node/7)

All true with 9.10, but I don't know whether this is the issue with the original poster's problem on 9.04.

---

