---
title: "Amarok Samba Collection problem"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by mcarden on 2008-04-05
I am running Amarok 1.4.7 on Feisty via KDE 3.5.6.

I have audio stored on a local drive via /mnt/music and more audio stored on another machine via a Samba mount at /mnt/podcast

Amarok's [Settings -> Configure -> Collection] has both locations selected but [Tools -> Rescan collection] finds and indexes only the local content and none of the Samba mounted content.

The Samba mount is working to the extent that I can navigate to it in Konqueror and write, read and delete a new file there. I can also read all the other content there.

In Amarok, if I use the Files tab in the interface, I can see and play all of the contents of /mnt/podcast. It's just that Amarok refuses to add them to the Collection, so copying to my portable player involves manually clicking through folders in the Files menu to find things - hardly a sane way to use it.

Any ideas why Amarok won't index the content to its Collection?

---

### Post by OoooMatron on 2008-04-05
It has never worked like that. There is a work around for samba connections and it involves writing a line in fstab but i cannot remember exactly what you need. I am sure it's on the amarok faq or forum.

Even then, it's very problamtic, so much so I gave up with Amarok complelely and now just use Gnump3d as a server and totem for my client.

---

### Post by mcarden on 2008-04-05
<quote>There is a work around for samba connections and it involves writing a line in fstab but i cannot remember exactly what you need. I am sure it's on the amarok faq or forum.</quote>

Indeed there is a page on the Amarok wiki that deals with Samba. It's where you can find out how to make sure that your Samba mount is properly mounted by /etc/fstab so that the files are available locally. You'll note from my query that I have done so and that even Amarok itself can access the location via its File tab.

Initially I considered that perhaps it's important for Amarok to be able to *write* the location in order to index it (though there's no mention of that on the Amarok wiki) but again you'll see from my original post that writing is not a problem.

I have seen Amarok indexing a collection from a Samba mount, so I know that it can work like that. Just not for me with this current setup.

---

