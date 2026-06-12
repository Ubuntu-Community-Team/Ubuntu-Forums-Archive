---
title: "Amarok, mtp and a Zen: can't transfer some files..."
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by doundounba on 2007-04-27
Hi all,

Just this morning I received a brand new Creative Zen V Plus player.  I upgraded one of my boxes to Feisty, reading that the bundled Amarok version has MTP support built in.  And it does.  It sees my player just fine.

However, in the process of uploading files to the player, I am having some difficulties.  Many files - usually with accented or other 'odd' characters in either the artist name, the album name or the song title (and consequently in the file name) - are not transferring to my player.  In fact, a lot of my favorites won't transfer. :( 

I've done a little digging, and found something (see [>here<]("http://www.misticriver.net/showthread.php?t=50579")) that says:
> 
However there is a "slight" problem with character encoding. Amarok uses by default ID3Tags version 2.4, this means that it uses LibTag as the backend for handling the Tags, but this also poses a problem for "older" ID3Tags v1 and 2.3, making the tags incompatibles with v1 and v2 (up to 2.3) compatible players (XMMS, Audacious, etc). The problem has got to do with character encoding. UNICODE character encoding in 2.3 tags (EasyTag uses 2.3) uses UTF-16, where as 2.4 uses UTF-8, even though Amarok is capable of understanding correctly these tags, the problems arise when you try to sync your files, as the tags will be missread, and some files will fial to sync (especially those files with non-standard characters, like accentuated characters, Asian language encoding, etc), so you will have to either update your tags or change them. Being a Spanish speaker, I stumbled onto this problem rather quickly. I don't know if by forcing the characters to be in ISO format has any better results than UNICODE.


Does anyone know if/how this can be fixed? Is there an easy way to "sanitize" the ID3 tags and filenames from the command line?

Any help/hints would be greatly appreciated.

---

### Post by mendieta on 2007-07-27
I just found your post in a search. I am having the same problem. I couldn't find a way to fix all the characters from the command line. But I tested with Gnomad2, and it transfers files with Spanish characters just fine. It owuld be great to have a better solution (Amarok is a lot more intuitive). But in the meantime, this is a workaround

Cheers!

---

### Post by MeneK on 2007-08-02
I have the same problem. There is a bug report for this issue at [http://bugs.kde.org](http://bugs.kde.org) :

[http://bugs.kde.org/show_bug.cgi?id=139722](http://bugs.kde.org/show_bug.cgi?id=139722)

---

