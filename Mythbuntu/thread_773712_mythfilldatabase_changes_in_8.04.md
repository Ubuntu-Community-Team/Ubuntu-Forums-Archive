---
title: "mythfilldatabase changes in 8.04?"
date: 2008-04-29
forum: Mythbuntu
---

### Post by zeltak on 2008-04-29
Hi all

Up until the 8.04 upgrade i was able to get my EPG data from a XML file (since i dont live in a country with a EPG support) using this command:

mythfilldatabase --file 1 -1 /home/zeltak/.wine/drive_c/Program\ Files/MegaEPG/xml/epgdata.xml 


Ever since the upgrade i get this error when i run the command (which prevously ran perfectly)

2008-04-29 09:24:49.679 Bypassing grabbers, reading directly from file
illegal option: '/home/zeltak/.wine/drive_c/Program Files/MegaEPG/xml/epgdata.xml' (use --help)
2008-04-29 09:24:49.680 DataDirect: Deleting temporary files


What has changed since the upgrade? can anyone help on this issue?

thx alot in advance

Zeltak

---

### Post by mrand on 2008-04-29
> **zeltak said:**
> Hi all

Up until the 8.04 upgrade i was able to get my EPG data from a XML file (since i dont live in a country with a EPG support) using this command:

```
mythfilldatabase --file 1 -1 /home/zeltak/.wine/drive_c/Program\ Files/MegaEPG/xml/epgdata.xml
``` 


Ever since the upgrade i get this error when i run the command (which prevously ran perfectly)

```
2008-04-29 09:24:49.679 Bypassing grabbers, reading directly from file
illegal option: '/home/zeltak/.wine/drive_c/Program Files/MegaEPG/xml/epgdata.xml' (use --help)
2008-04-29 09:24:49.680 DataDirect: Deleting temporary files
```


What has changed since the upgrade? can anyone help on this issue?

Howdy Zeltak,

The short answer is that many, many things have changed.

The usual answer when XML is involved is that there is something in your XML file that mythfilldatabase doesn't like.  First off, it must absolutely be XML compliant ([read this mailing list thread]("http://www.gossamer-threads.com/lists/mythtv/dev/325599")).  Then in addition, there *might* be a limitation on whitespace placement.  Here is a quote from a private email conversation I had with another user a while back:

> mythfilldatabase ought trim leading and trailing spaces (and EOLs) from all strings it gets from the xml-file. XML specification is very vague in this regard.

For instance you can have title encode like this:
<title>Star Trek VII</title>

or like this:

<title>
Star Trek VII
</title>

or even like this:

<title>
       Star Trek VII
</title>

Its obvious that all of the forms above describe the same program. However, depending on the parsing
framework used, you might need to trim spaces. And that's the problem with the current version of
mythfilldatabase.

Hope that helps!

   Marc

---

### Post by callagga on 2008-05-19
I'm getting the same problem.  Did you find a fix zeltak?

I'm getting:

```
greg@mythtv:~/.shepherd$ 
greg@mythtv:~/.shepherd$ mythfilldatabase --update --file 1 -1 output.xmltv 
2008-05-19 20:41:00.937 Bypassing grabbers, reading directly from file
illegal option: 'output.xmltv' (use --help)
2008-05-19 20:41:00.938 DataDirect: Deleting temporary files
greg@mythtv:~/.shepherd$ 

```

---

### Post by zeltak on 2008-05-19
Hi

No I have not fixed it yet. I tired a few different xml epg grabbers but none worked...does anyone know whats wrong..it used to work so well with all previous mythtv versions (0.18,0.19,0.20...)?

thx

Zeltak

---

### Post by laga on 2008-05-19
Remove "-1" from your mythfilldatabase call.

---

### Post by zeltak on 2008-05-20
WoW, Thx Laga!!!

I cant believe it was that simple...now it works!!
I have gone almost 3 weeks with no EPG but now its fixed! i think this should be sticky (or in the wiki) so other people don't encounter the same problem!

thx again

Zeltak

---

### Post by callagga on 2008-05-20
didn't work for me :(

Posted my issue here [http://ubuntuforums.org/showthread.php?t=800696]("http://ubuntuforums.org/showthread.php?t=800696")

---

