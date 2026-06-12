---
title: "Shoutcast in Listen Music Player 0.5"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by IceReaver75 on 2008-03-13
I just installed Listen and when I click the shoutcast button under webradio nothing shows up at all.  Does anybody know why this might be?  I can manually enter radio streams by URL address.  ANy help on this will be appreciated. Thank you

---

### Post by IceReaver75 on 2008-03-13
when I start listen in a terminal this is what is get if thats any help:

/usr/lib/listen/listen.py:154: GtkWarning: gtk_tree_model_get_iter: assertion `path != NULL' failed
  gtk.main()
/usr/lib/listen/listen.py:154: GtkWarning: gtk_list_store_set_valist: assertion `VALID_ITER (iter, list_store)' failed
  gtk.main()
-> [http://www.shoutcast.com/directory/?numresult=25&startat=0&sgenre=TopTen](http://www.shoutcast.com/directory/?numresult=25&startat=0&sgenre=TopTen)
Stream OEF 1 False
E:ShoutcastBrowser:Failed to retreive categorie list


am I missing some dependencies or anything like that?

---

### Post by uwehauck on 2008-03-18
I get the same error when trying to select any channel from shoutcast. Empty window and no radio stations at all.
Has there been some update recently ?
Greetings
Uwe

---

### Post by prince_niceguy on 2008-06-18
Am too having the same problem.. I like amarok where in it populates all the stations from shoutcast without me doing manual work... is there any such alternate on gtk based players?

---

