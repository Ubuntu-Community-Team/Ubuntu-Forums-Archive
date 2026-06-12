---
title: "Totem requesting DVD source"
date: 2020-02-26
forum: Multimedia Software
---

### Post by lwalper on 2020-02-26
When I insert a DVD into the DVD disk player Totem opens with the warning "DVD source is required to play file, but is not installed."

There are then two options given:
"Find in Ubuntu Software" and
CANCEL

When I click on the find software option I get the warning

"Unable to find the requested software" and the disk will not play.

Where do I get the required software?

---

### Post by Yellow Pasque on 2020-02-26
Did you do this?:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by lwalper on 2020-02-26
> **Yellow Pasque said:**
> Did you do this?:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Actually, no I had not done that. I followed the procedure described above and links provided. I have now installed libdvd-css and get the same result. Guess I'll use VLC since it works.

Thanks for the assist.

---

### Post by deadflowr on 2020-02-27
You most likely need the gstreamer "bad" package.
[https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1809044]("https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1809044")
scroll down to comment #8.

The package is installable through the Software Store, fwiw.
It's in Add-ons >> Codecs.
But it'll take a minute to locate since the Software store shows very generic entries for all the gstreamer plugins.

---

