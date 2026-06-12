---
title: "MythTV database (channel/listings) problems"
date: 2007-10-24
forum: Mythbuntu
---

### Post by prion on 2007-10-24
Dear friends,
     I'm having some problems giving my listing and channel information to the mythTV DB.  I am using custum-generated XML files and the command:

mythfilldatabast --file 1 -1 listings.xml

The channels are listed by name, but do not have a number associated with them.  The listings are not present.  Has anyone encountered a problem like this before?  I am using the specifications in the XMLTV.DTD.

Here is a sample of my XML file:

<tv>
<channel id = "4.cable">
<display-name>4 - KNBC</display-name>
</channel>
...
<programme start = "200710220400" stop = "200710220500" id = "2.cable">
<title>CBS Morning News</title>
</programme>
</tv>

I appriciate any help on this topic.  I can't wait to have a MythTV box !

_prion

---

### Post by prion on 2007-10-25
I fixed a problem in the XML <programme> tag, the id attribute should be channel.  Now I have listings when I use the frontend and search for shows by title.  When I try to search listings by channel, there is only <unknown> listings.  Any ideas?

---

### Post by napsilan on 2007-10-25
have you tried mythfilldatabase --manual?

---

