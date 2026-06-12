---
title: "How to tag an mkv file?"
date: 2010-09-19
forum: Multimedia Software
---

### Post by ron999 on 2010-09-19
Hi
Has anybody had success applying tags to an mkv file?

In this example here:- [http://www.matroska.org/technical/specs/tagging/example-video.html]("http://www.matroska.org/technical/specs/tagging/example-video.html")
It shows how to add a simple tag using an xml file.
And some more information here:-[http://manpages.ubuntu.com/manpages/jaunty/man1/mkvmerge.1.html]("http://manpages.ubuntu.com/manpages/jaunty/man1/mkvmerge.1.html")


For example:-

This is the xml file for Dune:-

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE Tags SYSTEM "matroskatags.dtd">
<Tags>
  <!-- movie -->
  <Tag>
    <Targets>
      <TargetTypeValue>50</TargetTypeValue>
    </Targets>
    <Simple>
      <Name>TITLE</Name>
      <String>Dune</String>
    </Simple>
    <Simple>
      <Name>DIRECTOR</Name>
      <String>David Lynch</String>
    </Simple>
    <Simple>
      <Name>DATE_RELEASED</Name>
      <String>1984</String>
    </Simple>
    <Simple>
      <Name>COMMENT</Name>
      <String>Great sci-fi movie</String>
    </Simple>
  </Tag>
</Tags>
```

So that file is saved as **dune.xml**

Then you have your movie **foo.mkv**

And use a command like this:-

```
mkvmerge -o output.mkv --global-tags dune.xml foo.mkv
```

That's supposed to tag the **output.mkv** file with the information.
But I can't seem to get it to work.
When it's finished I would expect to be able to read the tags using mediainfo or with VLC's > Tools > Media information.

I've also tried tagging using the mkvmergeGUI, by adding the xml file in Global > Tag file
Doesn't seem to work either.

---

### Post by Bonster on 2010-09-20
No go here either, it dont work, same goes for the VLC metadata, it doesnt save

---

