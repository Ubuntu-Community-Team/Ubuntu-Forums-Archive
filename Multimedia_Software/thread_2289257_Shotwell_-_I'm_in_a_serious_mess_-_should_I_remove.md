---
title: "Shotwell - I'm in a serious mess - should I remove, and re-install?"
date: 2015-08-02
forum: Multimedia Software
---

### Post by Ace..... on 2015-08-02
The long and the short of it is: I've got multiple time lines (in shotwell), and a massive quantity of duplicate photos.
It's obviously my fault..... but it stems from the problem of failing to understand the implications of 'copy' and 'import' and the lack of a 'move' option...... at least I can't find it.

I've got space on my hard drive.... but not on my bakup drive...... so I can't bakup 'home'.

What I'm thinking..... is to simply copy all the photos from the different directories, into a single directory...... thereby eliminating all copies.....
.... then have shotwell move everything into date created directories.

This will allow me to delete all other instances.

If I remove shotwell, and reinstall it....... will it do this?

OR

Maybe I should move everything into a single directory...... and let shotwell organise the time line, but without creating directories...... so all the photos remain in one directory.

Presuming that shotwell can create a timeline of years months and days, without needing to place the files in associated directories...
...what's best?

Everything in one directory?
Or is it best to move files into date associated directories?

---

### Post by PaulW2U on 2015-08-02
*Thread moved to **Multimedia Software**.*

---

### Post by Ace..... on 2015-08-02
I've been having a think about this organisational problem.

It appears that there are photo groupings, that you just want in the same directory - a project that's not 'time relevant'.
AND
There can be problems with standard chronological type family photos, when they cross over the month/month.
If Shotwell creates directories by month..... groupings are separated.

I know Shotwell allows group creation..... but they'd still be stored in different dirs.
If the 'family type' pics went into one directory, they could easily be grouped by ones favourite file manager

Is this just me..... am I failing to utilise effectively the grouping app...... or am I right to think in terms of fundamental file management (vis a vis directories)?
But then..... putting all the files in one directory...... I don't see any negs; it's just a file listing.
The names are just numbers, but in file working mode I can use an image viewer, which all have got 'forward and back'.

So I think that's it.
Don't let shotwell create directories, but rather let it use the dirs. it's given.
That will mean, a number of special photo dirs. and one big one for life...... or perhaps a small number of major event dirs. like before and after a birth, batchelor/married/old family etc.

When naming the dirs.... simply give them a number, and they'll be organised chronologically.
That way, they'll be accessible by file, as well as being presentationally organised in Shotwell.

Once I'm done, I'll remove shotwell and re-install.
I wonder if some stubs are left behind..... like config files that hold on to personal settings....... those would need to go.

(Edit: Thanks Paul for finding the thread a home :) )

---

### Post by Ace..... on 2015-08-03
**What I can tell you, is that I haven't found an easy solution to this problem.**
Maybe some serious 'compare' progs are required.

Other than that, it is all down to planning, before doing anything.
In effect, a correct balance between the need to act, and the need to prepare.

**Command line:** I think it's a no go (without serious consideration).
I researched this, but in all cases, there was a lack of confidence regarding file names...... and rightly so.

**Warning:** If a camera has been reset, it will take photos with the same name.
Or maybe you've received photos from a third party, named as yours are named.
Here lies the advantage of different dirs.

**How did I do it?**
I used Krusader.
It's an absolute balls ache, but I had 2 panels open - left the source tree, right the single dir. (repository)

I drilled down to the first 'day dir,' and moved the files.
Went up and deleted the dir. (top dir)
The new top dir could then be d-clicked, and the files moved - go up and delete the dir - and repeat.

You do get quick at doing this

The great thing with Krusader, is that when a file name clashes, you can see the two photos, and choose to skip, or 'suggest new name' then 'rename'.
This can happen often!

So I emptied each 'day dir', deleting as I emptied, until I could delete the month.... and finally the year.

Any 'same named files' have got a 1 (etc.) added.... so that's fine.
The primary shotwell photos, from the photo/year/month/day/tree are now in one dir.

**What's the remaining problem?**
I have a second tree of photos. 

Using Krusader again, I accessed properties for each year dir. - gaining the total file number.
I then highlighted that year of files in the right window - all in one repository (to gain total file highlighted).

Overall... I've got around 100 extra files in the second tree.

Some will be skipped files..... but did I skip that many......... I don't know because I clicked repeat for all instances, when originally skipping the files.

To verify all files will mean, once again, drilling down to 'day dirs'.
I don't think that I can do it twice :(

I may write off the extra images..... say 50-70, out of 4600.
Before I do that, I'll research the add on 'compare software' for Krusader.

Overall.... it's a nightmare.

The only ideal way to do it, would be to have a script that moves all files in the chosen tree, to the repository..... renaming files that are different but have the same name...... and skipping files that are the same (regardless of name).

This way, any tree could be dumped into a repository..... and all files that successfully move, would be different.
Any remaining files and dirs would be deleted.

I wonder if any software has been written to achieve that?

:)

---

### Post by Ace..... on 2015-08-05
I've just started a thread on the shotwell mailing lists

After a bit of background, here's what I'm asking:

> *What I Need To Do*

*.... is to compare all the files in a dir tree, with the files in the repository dir.*

*I need to end up with a list of files in the left pane, that don't exist in the right pane.*
*File names don't count, because we know that different photos have the same file name.*
*It's the file data that must be different.*

[I]I could then move all the files from the left pane, into the right pane.
[/I](Any same named files would go through the suggest rename process.)
*Then delete the source tree.*
*Job done.*


---

### Post by Ace..... on 2015-08-05
**Problem solved!**
I used Fslint.


This is a great program....... you paste in the repository path first.
On the next line you paste the path to the primary folder of the tree of sub dirs.


Click search........ every instance of duplicates is grouped.
In my case the file in the repository was top in each group.


Click select, within groups, 'all but first'.
Then delete.


It was as quick as that.


I'm now just tidying up.


:)

---

