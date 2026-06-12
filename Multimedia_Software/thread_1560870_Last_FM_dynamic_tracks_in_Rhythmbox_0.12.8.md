---
title: "Last FM dynamic tracks in Rhythmbox 0.12.8"
date: 2010-08-25
forum: Multimedia Software
---

### Post by MorrisseyJ on 2010-08-25
I am trying to get Last FM's dynamic tracks plugin to work in Rhtymbox 0.12.8 so that i can have a feature equivalent to the Genius function in iTunes.

I have found the following from OMG Ubuntu: [http://www.omgubuntu.co.uk/2009/12/auto-queue-similar-tracks-in-rhythmbox.html](http://www.omgubuntu.co.uk/2009/12/auto-queue-similar-tracks-in-rhythmbox.html)

I follow the instructions, but run into problems when i can't find a rhythmbox folder at:  > /home/USERNAMEHERE/.gnome2/rhythmbox/

Instead the only plugin folder i can find is at:> /usr/lib/ruthymbox/plugins/

The problem is that when i try to move the extracted Last FM plugin to > /usr/lib/ruthymbox/plugins/

i get the message:

> There was an error moving the file into /usr/lib/rhythmbox/plugins. Error moving file: Permission denied

Can anyone tell me where i need to stick the Last FM plugin so that i can get dynamic tracks to make playlists in Rythmbox. Also getting reccomendations from LastFM on anything that i am playing in Rythmbox (like in Guayadeque) would be great.

Thanks.

---

### Post by dv3500ea on 2010-08-25
Don't install it this way.

Instead, install the package [rhythmbox-plugins]("apt:rhythmbox-plugins").

Then, in rhytmbox, go to Edit -> Plugins and enable Last.fm:

---

### Post by MorrisseyJ on 2010-08-25
Thanks but the problem is that that plugin doesn't, as far as i can see, enable dynamic tracks. It simply allows me to access my Last FM account from Rhythmbox.

If i have missed something here, it would be great if you could point it out.

---

### Post by MorrisseyJ on 2011-02-02
Solution is in libre scrobble

[http://www.omgubuntu.co.uk/2010/07/scrobble-to-libre-fm-via-rhythmbox/](http://www.omgubuntu.co.uk/2010/07/scrobble-to-libre-fm-via-rhythmbox/)

There are typos in the instructions so read the comments.

---

