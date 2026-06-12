---
title: "Become a documentation hero today! No application necessary."
date: 2010-02-19
forum: Mythbuntu
---

### Post by tgm4883 on 2010-02-19
The Mythbuntu documentation was recently migrated from the PDF to the new Mythbuntu wiki. The last update of the PDF content was around 8.10, so many of the items refer to MythTV 0.20. When Mythbuntu 10.04 comes out, it will have the latest and greatest MythTV 0.23.

Here we are in the last stretch before the release of 10.04 and
we're ready for everyone (users and developers alike) to chip in and find areas of the documentation that need major or minor cleanup! Some sections may need to be re-written completely, and others deleted altogether. You'll find placeholders for screenshots (we need new ones showing the very well received Mythbuntu theme). It's a wiki - so don't be shy! Working on it is as simple as:

[LIST=1]
[*]Visiting [http://www.mythbuntu.org/wiki](http://www.mythbuntu.org/wiki)
[*]Log in (easy is via OpenID, for example, [https://launchpad.net/~username](https://launchpad.net/~username))
[*]Edit!
[*]Become documentation hero
[/LIST]

Again, don't be shy; there is lots of work to be done - minor as well as major editing. Just do what is right for the project. If you have questions, feel free to send an email to this list, or stop by #ubuntu-mythtv-dev on freenode.

---

### Post by johnnybirdman on 2010-02-25
I would like to help.  Are changes moderated in some way prior to publication?
J.

---

### Post by tgm4883 on 2010-02-25
> **johnnybirdman said:**
> I would like to help.  Are changes moderated in some way prior to publication?
J.

No, it's a wiki. If needed, we can roll back changes that are made.

---

### Post by johnnybirdman on 2010-02-25
> **tgm4883 said:**
> No, it's a wiki. If needed, we can roll back changes that are made.

Thanks, that is what I thought. Just don't want to mess anything/one up.
J.

---

### Post by nhtrader on 2011-01-27
What is the proper way to upload screenshots?

I ask b/c I've experimented with ubuntus printscreen feature and it creates *.png images which are quite large. I like to show some screenshots but half the size of these png files. Plus these png files are approx 1.3 Mb each. 

How to I create smaller screenshots?

2. If I create a simple static HTML page, can this be uploaded into the forum?

---

### Post by tgm4883 on 2011-01-27
> **nhtrader said:**
> What is the proper way to upload screenshots?

I ask b/c I've experimented with ubuntus printscreen feature and it creates *.png images which are quite large. I like to show some screenshots but half the size of these png files. Plus these png files are approx 1.3 Mb each. 

How to I create smaller screenshots?

2. If I create a simple static HTML page, can this be uploaded into the forum?

You could use gimp to resize them or change them to another format. 

As for 2, I doubt you could upload an HTML page to the forum. The above wiki is where the documentation resides.

---

### Post by dibuntux on 2011-05-23
Apart from documentation, what about translation?

I see that in 0.24 italian translation is even worst than that in 0.23: not even the main menu is completely translated.

Is there a way I can get the text from the source and give it back translated to developers?

---

### Post by tgm4883 on 2011-05-23
> **dibuntux said:**
> Apart from documentation, what about translation?

I see that in 0.24 italian translation is even worst than that in 0.23: not even the main menu is completely translated.

Is there a way I can get the text from the source and give it back translated to developers?

Hmm, I don't know anything about translations. I'll ping another dev and see what the procedure is for things like that.

---

### Post by superm1 on 2011-11-11
I don't know the best way for this, but the way I would do it is to clone the tree, and then use a tool to translate to your locale language.

I think linguist is the best way (not positive though).
[http://doc.qt.nokia.com/latest/linguist-manual.html](http://doc.qt.nokia.com/latest/linguist-manual.html)

Once you've got translations together, commit them to the branch and then run git format-patch -1 to create a patch and submit that patch to trac.  You might want to check with mythtv-users mailing list to see if they have another recommendation on how to do it.

---

### Post by dibuntux on 2011-11-17
Thanks for your reply. Pretty cryptic for a non developer. I took a look at QT Linguist & I got questions:

1) Where do I get a .ts file to translate?
2) "commit them to the branch and then run git format-patch -1 to create a patch and submit that patch to trac" - have no idea of what you are talking about.

I think it should be easier than this...

---

