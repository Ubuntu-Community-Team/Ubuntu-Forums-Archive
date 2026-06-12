---
title: "Image thumbnail viewing with regexps?"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by Ces on 2007-10-10
Does anyone know of any image viewer/manager/organizer that is able to use regular expressions? And use them as categories/tags?

For instance, in the image viewers I’ve tried it’s a piece of cake to show all images in any directory in thumbnail view. What I wish for is being able to view just a subset of those images according to some kind of regular expression. And further being able to save those ”searches” between sessions.

I hope I’m making some sort of sense...

My interest lies in lightweight applications (no massive Gnome or KDE dependencies).

[CENTER]**[COLOR="RoyalBlue"] ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ [/COLOR]**[/CENTER]

Ugh. Let me give an example.

Assume I have a directory full of photos and drawings of insects. In a pane with a directory view I’m able to browse to this directory and select it (doing so results in thumbnails of all the images being shown in another pane). The usual behaviour.

Now then, since most of the images are named like **col43b - Insect Institute - A giant blue butterfly.png**, I wish to just show the images whose name contain the text “Insect Institute” (this is easily done with **grep** on a command line). Further I wish to save this regexp search as a ”tag” so I  with ease can come back to it later, in a well organized manner.

Exactly how this is done isn’t important, one possible way is to have a pane with a view similar to that of directory tree, but with the regexp tags in stead. For example:

```
+ Family Photos
- Work related tags
  - Insect archive
    - View by contributor
        Audumla Craig
        Insect Institute
    + View by species
```

And then selecting “Insect Institute” above you’re shown the relevant subset of thumbnails, as detailed above.


I’m not sure if this fictional example made my needs any clearer... In any case I’m looking forward to suggestions of image viewers.

---

