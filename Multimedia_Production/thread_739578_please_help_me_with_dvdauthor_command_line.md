---
title: "please help me with dvdauthor command line"
date: 2008-03-29
forum: Multimedia Production
---

### Post by hurtstotalktoyou on 2008-03-29
Hi, all.

I have a bunch of dvd-compliant *.mpeg files which I would like to burn to disc.  However, my cd burning software can only deal with *.iso images.  So, I thought I'd use dvdauthor cli to make the image, but I have no idea what commands to use.

Here's what the dvd structure must be:
1.  no menu
2.  play video as first action
3.  one title only
4.  chapters corresponding to the different source *.mpeg files

Can anyone help me with this?  I would be very grateful.

Thanks in advance!

---

### Post by Oldsoldier2003 on 2008-03-30
[http://dvdauthor.sourceforge.net/doc/index.html](http://dvdauthor.sourceforge.net/doc/index.html)

---

### Post by hurtstotalktoyou on 2008-03-31
This looks like the kind of thing I'd want to use:

<dvdauthor>
    <vmgm />
    <titleset>
        <titles>
            <pgc>
                <vob file="video1.mpg" />
                <vob file="video2.mpg" />
            </pgc>
        </titles>
    </titleset>
</dvdauthor>

([source](http://dvdauthor.sourceforge.net/doc/ex-title.html#AEN41))

However, these are not terminal commands, are they?  How do I run them?

---

### Post by cotcot on 2008-03-31
No these are not command line instructions. 
This is the xml file used by the dvdauthor command. See manual in the link from the previous poster.  [[COLOR="Red"]Here[/COLOR]]("http://gentoo-wiki.com/HOWTO_Create_a_DVD:Filesystem") is a howto on using dvdauthor.
Maybe you could check out apps such as devede, dvdstyler or qdvdauthor also.

---

