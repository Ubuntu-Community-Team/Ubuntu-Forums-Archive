---
title: "How to play my &quot;My  Recommendations&quot; lastfm station in rhythmbox"
date: 2008-06-02
forum: Multimedia Software
---

### Post by DexterLB on 2008-06-02
I have the rhythmbox last.fm plugin, it's scrobbling, everything's OK but I can only see the Neighbourhood station nd I can't find the Recommendations one. So, how can I play my "My recommendations" station?

---

### Post by DexterLB on 2008-06-02
Hallooooo
Can I play lastfm://xxxx links with rhythmbox?

---

### Post by dekaru on 2008-11-28
also, how do you play your own radio station ?

---

### Post by lelamal on 2008-12-14
> **DexterLB said:**
> I have the rhythmbox last.fm plugin, it's scrobbling, everything's OK but I can only see the Neighbourhood station nd I can't find the Recommendations one. So, how can I play my "My recommendations" station?

Hi, I am not a computer whiz, but this is what worked for me (but may not for you): on Last.fm website, login to your profile, then click on "Edit profile details". Click on the "Website" tab and chose "Play music in the Last.fm software(NOTE: Track previews will still play on the site.)" rather than "Play music in-page". Save, then get back to your profile page and choose "Recommended" from the dropdown menu with your picture (top right corner). When you click on "Play all Recommendations" it should ask you which application you want to choose, simply hit on Rhythmbox and set it as default. Finally, your playlist should now appear as "yourusername's Recommended Radio: (null) percent", which means nothing to me, honestly, but definitely does the job. Enjoy (hopefully)!
:guitar:

---

### Post by dekaru on 2008-12-25
Thanks lelamal, now I can play my recommended radio station from RB.

When I tried to listen to my personal radio station, though, the player paused and when I clicked on PLAY I got a warning that said:

"Couldn't start playback
Nothing to play"


Any idea for a workaround/fix ??

---

### Post by TheWitchdoktor on 2009-01-12
This worked for me (even personal station):

[http://lecaros.wordpress.com/2007/06/03/reproducir-recomendados-de-lastfm-en-rhythmbox/](http://lecaros.wordpress.com/2007/06/03/reproducir-recomendados-de-lastfm-en-rhythmbox/)

(it's in spanish)

---

### Post by Endolith on 2009-02-21
> **lelamal said:**
> When you click on "Play all Recommendations" it should ask you which application you want to choose, simply hit on Rhythmbox and set it as default. 

Isn't this a URL, though?  Can you give us the URL so we can just add it without changing last.fm settings?

There's a workaround here but it is said to not work anymore: [http://bugzilla.gnome.org/show_bug.cgi?id=373622](http://bugzilla.gnome.org/show_bug.cgi?id=373622)

---

### Post by lelamal on 2009-02-22
> **Endolith said:**
> Isn't this a URL, though?  Can you give us the URL so we can just add it without changing last.fm settings?

There's a workaround here but it is said to not work anymore: [http://bugzilla.gnome.org/show_bug.cgi?id=373622](http://bugzilla.gnome.org/show_bug.cgi?id=373622)

How do you check URL's in your radio station titles? When I right-click, the only option I'm given is to delete the station. The only thing that comes to my mind, now, in order to provide you with said URL is to do something you could do yourself, i.e. right-click on "Play all Recommendations" and copy the link location, which would be:
[HTML]lastfm://user/<yourusername>/recommended[/HTML]

[QUOTE=dekaru]Thanks lelamal, now I can play my recommended radio station from RB.

When I tried to listen to my personal radio station, though, the player paused and when I clicked on PLAY I got a warning that said:

"Couldn't start playback
Nothing to play"


Any idea for a workaround/fix ?? [/QUOTE]

Dekaru, I've got the same problem, and couldn't find a solution anywhere - I receive a slightly different message, "(null)", rather than "Nothing to play", but I guess what matters here is the (lack of) result. I'm starting to think that it's not currently possible to use this feature.

---

### Post by Endolith on 2009-02-22
> **lelamal said:**
> which would be:
[html]lastfm://user/<yourusername>/recommended[/html]


That works! Thanks

---

