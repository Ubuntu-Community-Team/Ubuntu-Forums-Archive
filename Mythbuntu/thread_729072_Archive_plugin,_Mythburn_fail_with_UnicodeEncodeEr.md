---
title: "Archive plugin, Mythburn fail with UnicodeEncodeError"
date: 2008-03-19
forum: Mythbuntu
---

### Post by exprezzz on 2008-03-19
Hi, 

I upgraded to mythtv 0.21 on march 11. Since then, i couldn"t burn DVD with mytharchive if an european accent appears in the title (or description?).with en error like 
---
File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 5400 in paiun processJob(job), [...] line 5196 in processJob BurnDVDISO(title) [...] line 2587 in BurnDVDISO write(command) [...] line 242 in write sys.stdout.write(text+"\n")
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe0' in position 61: ordinal not in range(128)
--- 
It's not a cut-and-paste, but i can'tt find the good logfile...

I'm discovering python, so i went to the sources, (/usr/share/mythtv/mytharchive/scripts/mythburn.py) and change line 5196 with : 
                BurnDVDISO(title.encode("utf-8"))
(i added the <<.encode("utf-8")>> part)

I don't know it it's an awful hack or a good way to solve the problem, i have no "full view" of the source.
It's worked for me, and until now... Use it at  your own risk (you must be superuser to modify the file, it meens it's dangerous :-) )

---

### Post by Nikas on 2008-03-19
Yes. I have the same problem. :(
Really want to burn stuff. My space are running out.

I will try your "hack" :) Thanks!

---

### Post by Nikas on 2008-03-25
The hack did not work. I have"-" and non ascii chars in my descriptions but i found the solution (done today).

This is for .21

The problems are fixed in .21-fixes and i just changed the mythburn.py to the latest from the .21-fixes branch.

```

# cd  /usr/share/mythtv/mytharchive/scripts/
# rm mythburn.py
# wget http://svn.mythtv.org/trac/export/16784/branches/release-0-21-fixes/mythplugins/mytharchive/mythburn/scripts/mythburn.py

```

Changes: [http://svn.mythtv.org/trac/changeset/16783](http://svn.mythtv.org/trac/changeset/16783)

Works great!

---

