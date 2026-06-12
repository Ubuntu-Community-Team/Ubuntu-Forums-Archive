---
title: "How Can I set tag in Amarok by dcop ?"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by Me! on 2008-01-22
Hi
I want to make small script in amarok by Bash , How can I set tags (album , title ,...) by dcop ?

Thanks

---

### Post by kko1 on 2008-01-22
Hello.

I'm not sure you can, but I'm not an expert neither on dcop nor Amarok, and I'm using an old Amarok version. I'll offer my 2 c anyhow. ;)

I spent a while browsing amarok's dcop calls by an application called *kdcop* - with amarok version 1.4.3 (Dapper) - and found that there's an easy way to *query* the tags, but not *set* them, if by "set" you mean "change" the tags stored in the files.

For tagging the files there are better programs, although I'm not sure I understood you right, so... do you want to tell what exactly do you want the script to do?

kko1

---

### Post by Me! on 2008-02-13
> **kko1 said:**
> Hello.

I'm not sure you can, but I'm not an expert neither on dcop nor Amarok, and I'm using an old Amarok version. I'll offer my 2 c anyhow. ;)

I spent a while browsing amarok's dcop calls by an application called *kdcop* - with amarok version 1.4.3 (Dapper) - and found that there's an easy way to *query* the tags, but not *set* them, if by "set" you mean "change" the tags stored in the files.

For tagging the files there are better programs, although I'm not sure I understood you right, so... do you want to tell what exactly do you want the script to do?

kko1

OK

I hope to write a script to retype Tags in Arabic characters to {English Arabic} , due to All mp3 players not supporting Arabic characters

I write the script to change Arabic -> English Arabic 
but it works on the files not in the Tags

If you (or any human) can help me to editing tags by script in Amarok or any where , I'm waiting

Thanks

---

### Post by kko1 on 2008-02-20
Hello again.

Ok, if I understand you right, you want to change the tags from arabic *letters/characters* to show the "same" (translitterated) in latin/roman *letters/characters*.

And you have already done this for the filenames?

Now, I think this can be solved by going around the problem. (There may be other options, but the solution I suggest seems quite easily workable.) Especially, if the filenames contain **all** the relevant tag information, that is:
- artist
- song name
- album name.

There are easy tools that can change tags based on the filename, **and**, conversely, rename files based on the tags. The one I have used myself is *easytag*. I am *not* sure it can handle all different types of characters, but you can try.

Two cases.

1) If your **filename** already contains all the wanted information, *and* is in latin characters:
- Use *easytag* (the "scanner" -> "fill tag(s)" feature) to "pick" the information from the filenames and change the tags accordingly.

2) If your **filename** does *not* contain all the information, or is in arabic characters:
- First use *easytag* (the "scanner" -> "rename file(s)" feature) to rename the files to contain all the information (from the tags).
- Then use the script (that I assume you have) to change the *filenames* to the latin alphabet.
- Lastly, use *easytag* (the "scanner" -> "fill tag(s)" feature) like in case 1 to "pick" the information from the filenames, and change the tags accordingly.
(- Finally, if you don't want to keep all that information in the filenames, you can of course rename them again with the same program. *Easytag* can also re-organise the files in a (new) directory structure, based on the tags.)

*

NOTE: *easytag* can handle large groups of files at once, if the filenames follow a similar pattern and/or the tag information exists. **Please be careful however, and try first with a small group of files, so you know you will get the results you want.**

I hope this helps you achieve what you aimed for.

kko1

---

### Post by Me! on 2008-05-17
Thank you kko1

But I want to make it as plug-in to one of famous audio player.

The Script is not for Me! only , it is for Arabic in Linux environment.

Thank you

---

