---
title: "Rhythmbox plugin:  A method to sift and remove duplicate songs?"
date: 2009-02-23
forum: Multimedia Software
---

### Post by xl_cheese on 2009-02-23
As the title says.  Is there a plugin that will easily sift your library to help you remove duplicate songs?  

Ex/  you have a song somewhere in your music lib and then copy a new greatest hits CD into it, but now you have two copies of the same song?  With hundreds of songs it's hard to manually remove these copies.

---

### Post by Stochastic on 2009-02-23
Moved to Multimedia & Video.

---

### Post by dannyboy79 on 2009-06-29
also wondering about this! please help.

---

### Post by uncibex on 2009-07-30
-bump-
Haven't been able to find an answer to this either

---

### Post by dannyboy79 on 2009-07-30
go to the bash irc channel on freenode.net and ask someone to help you write a bash script to find and remove duplicates. that's what I did but I forget what the code was.

---

### Post by freakalad on 2009-09-17
*bump*

also looking for a plugin to achieve the same result

---

### Post by phillychease on 2010-01-10
*bump* 
im lookin for the same thing.
or does anyone have the script?

---

### Post by scrawl on 2010-01-20
Anyone still interested in this?

I also wondered how to do this. It's not only that I have duplicate files, I sometimes have the same song from different sources, so the file name won't help. Doing this by hand is not acceptable when you have a huge music library. We would need a plugin that scans for duplicates based on the ID3 Metadata, with a smart algorithm.

Since I'm already familiar with Rhythmbox, I could go for it and make a plugin, if there still is any need.

---

### Post by freakalad on 2010-01-20
> **scrawl said:**
> I sometimes have the same song from different sources, so the file name won't help.

One of the best (if not *the* best) media managers that I've found, especially for *extremely* large collections, is MediaMonkey.
Unfortunately it's windows-only, but it runs fine in wine & a VM

Is allows for the mass/bulk renaming, moving & tagging of extremely large collections, and has a VERY cool function where it's able to locate duplicate titles & contents. 
I think the ability to locate duplicate content, is achieved by creating some sort of MD5 hash of the track & then comparing it tho other hashes. It's also able to find names for tracks that you have no idea what it may be.

Very cool piece of software & I've not found anything remotely as useful, anywhere else

- J

---

### Post by scrawl on 2010-01-21
Sounds very interesting. However it's not possible to get the similiarity of two songs by generating the MD5 sum. You just know if the files are exactly the same or not.

 I think it should be no problem to compare the MD5 hashes of the songs, thus I will include the MD5 check when the rest of the plugin is finished.

---

### Post by freakalad on 2010-01-21
> **scrawl said:**
> However it's not possible to get the similiarity of two songs by generating the MD5 sum.

Well, it uses some sort of hashing algorithm to compare songs (think it even references some sort of online library).

What I do know is that it's very successfully found the same songs with different names in different locations (and even sometimes different lengths & bit-rates, but the latter I think may be done by filename or tag comparison)

Whatever the case, it's a remarkable piece of software, for a modest price what it does for you, and I've not found anything that remotely comes close to it in any other software or platform. 
Theoretically, SingBird may eventually be able to achieve this with similar results, but that's still a long way off

---

### Post by scrawl on 2010-01-26
Alright, here's what I'm currently at. It's able to find duplicates with similiar audio tags, and remove them. In the near future I'll implement a md5sum of parts of the file, so it can detect them independant on the tags.

How to use it: Unpack the attached archive to $HOME/.gnome2/rhythmbox/plugins (create the folder if it doesn't exist yet) and activate "duplicate finder" in Rhythmbox plugins. Then select Tools -> Find duplicates in the menu.

I appreciate any feedback :p (Please tell me, if it works for you)

If anyone wants to improve the comparison algorithm (it's quite slow and dirty at the moment) feel free to submit code at [https://code.launchpad.net/~scrawl/rhythmbox-duplicate-finder/trunk](https://code.launchpad.net/~scrawl/rhythmbox-duplicate-finder/trunk)

---

### Post by freakalad on 2010-01-26
Sweet!

nice 1, thanks!

---

### Post by scrawl on 2010-01-26
So, does it work for you?

---

### Post by scrawl on 2010-01-26
I've just done a minor bug fix (files wont disappear from the duplicate list if you choose to delete them), attached new archive.

and, here's a screenshot, as a "proof" that it works :D

---

### Post by freakalad on 2010-01-26
> **scrawl said:**
> So, does it work for you?

note quite, but I still need to do some more testing

---

### Post by freakalad on 2010-01-27
MM is great, because it is a media manager for large volumes, not merely for locating duplicates.

If all you want to do is locate duplicates, the are better apps for win; the best I've found thus far is Beyond Compare.

But this is a POSIX world, and as such the "correct" way of locating duplicates is probably using diff

---

### Post by Rob T on 2010-02-01
It apears to work, but whenever i click on the move to trash icon, it just closes my rthmbox alltogether :@

---

### Post by scrawl on 2010-02-01
Console output?

I guess it's a Rhythmbox bug. Because whatever a plugin does, Rhythmbox should not crash...

---

### Post by nuzeb on 2010-04-20
Nice idea. I'll give it a try!

---

### Post by cynpeterson on 2010-04-21
This program causes mine to freeze up. Is there anyway to fix it?

---

### Post by scrawl on 2010-04-22
To anyone having problems with it: It was quite an experimental plugin. Maybe I'll rewrite it soon from scratch, it should be much faster then, also.

---

### Post by mihai.ile on 2010-05-04
Ok I tested the plugin, it has it's bugs but aside from that, I think it's has a very very ban implementation.

Here is why:
- bad integration with the application
- uses an additional popup like window
- reinventing the wheel (omg play buttons, additional lists, etc)
- add an extra top level menu (why? really needed?)
- oh and it crashes (but this I understand, implementation is not easy, don't blaim)

So what should we do about it?

Here is what I think the Duplicate-finder should be:

1) With the plugin activated, under the Music menu, we get an additional option to scan for duplicate files:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155458&stc=1&d=1272989730[/IMG]

2) A new entry is created and selected in the library section of rhythmbox where the contents of the list are the duplicated files (I mean the 2 files are listed one below the other, just like in normal playlist) and the files start to appear with search being done in a second thread avoiding breaking the whole user interface. Here, as we are used to rhythmbox lists, we can play the file by double click (imagine one may be an mp3, the other the flac version), we can do right click and see the file properties, you know the way rhythmbox works:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155459&stc=1&d=1272989730[/IMG]

3) The user does an right-click and then selects to remove or move to trash the selected file (here we could really have the both options, as rhythmbox supports/uses it already, in my mockup I only added remove option:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=155460&stc=1&d=1272989730[/IMG]

4) The library entry created ("Duplicates") supports a right click menu and has an option to be closed and totally disappears, until the user uses the feature again by invoking it in the music menu.

Now in my opinion, this would be a really good implemented feature, this is how I see it work best.
Of course those are only some mock-ups I made, suggestions are welcome.

---

### Post by scrawl on 2010-05-04
Hi mihai007,

thanks for your criticism. As you might have seen the plugin was rather an experiment than an end user application. Aside from that, I really like your mockups and the idea of packing the duplicate list into an extra source.

I think your mockups describe perfectly how it should be at the end. Just one additional "feature" I would take into consideration: An option to automatically scan for duplicates in the background whenever a file is added to the library.

I hope I can start working on it this weekend and start to make the mockups reality :)

---

### Post by mihai.ile on 2010-05-04
Great Idea, actually this option would be implicit, because as long as the user does not close the source, the plugin will automatically scan when importing files. This way you don't even need an additional option for the feature, it just works. I think it is normal for the source to be updated on every import if the user did not close it.

---

### Post by mihai.ile on 2010-05-04
Oh, here I have a small plugin I created just to add a source and select it automatically in rhythmbox, maybe it saves a little time when implementing...

Unfortunately I don't know almost anything about python so I can't help that much.

---

### Post by scrawl on 2010-05-04
> 
Oh, here I have a small plugin I created just to add a source and select it automatically in rhythmbox, maybe it saves a little time when implementing...

Thanks, thats actually a big help for me since I don't know anything of the Rhythmbox Source API yet.

My suggestion for the interface would be the following
 - on first start of the plugin or when importing a file, it automatically scans for duplicates in the background, so there is no need for a menu entry
 - if duplicates are found, the source is displayed, else the source wont be visible, so its consistent with Rhythmbox' "Missing files" source
 - The popup menu for a duplicate contains the entries "Mark as non-duplicate", "Remove from library" (removes entry from the library, doesnt delete file), "Move to trash", and "Properties" (launches standard RB properties dialog)
 - Another thing we have to keep in mind is that, when there are 2 similiar songs, the one with the lowest bit rate or file size is marked as the duplicate 
 - Columns in the duplicate source: Title, Artist, Album, Duplicate of
 - Via the preferences of the plugin you can adjust the checks that are performed to recognize duplicates so they fit best for your library
 
If you got any further ideas, please let me know :)

---

### Post by mihai.ile on 2010-05-04
I think that for the start it is a great set of features.

I do not know how the search algorhythm works (I saw your comments, seems Ok) but to improve a little, maybe it is possible that for every song you search forward for duplicates, before comparing the song with the rest of the library (which is quite slow) I don't know if would be possible to do a rhythmbox search for it's possible duplicate, bacause you can see rhythmbox has no problem searching instantly for a specific song. Maybe this would avoid comparing everything to everything. I don't know if rhythmbox has such search api visible for python plugins. But it would improve the search speed a lot, I think.

What I usually do always is look at the existing plugins and how are they made, usually gives good inspiration on how rhythmbox api works.
[http://live.gnome.org/RhythmboxPlugins/ThirdParty](http://live.gnome.org/RhythmboxPlugins/ThirdParty) is a big list of plugins and also, /usr/lib/rhythmbox/plugins contains the ones that came with ubuntu, all sources included. From there maybe Magnatune and Jamedo plugin has somthing to do with rhythmbox sources.

Oh and yes, the mark not duplicate will come handy when constantly searching for duplicates.

---

### Post by scrawl on 2010-05-04
Well, I am aware that the search algorithm of the previous plugin was really slow. Comparing everything to everything gets even slower on large libraries, with the library I had back then it was no problem, but with 2000+ entries it doesnt seem to make any progress at all.

The new algorithm should work like this: It should first sort all entries by title, Then compare entry 1 and 2, then 2 and 3, 3 and 4, and so on. This way the amount of comparisons required is roughly the amount of songs you have in your library.

I won't go deeper into the algorithm here, I'll then just start working on it and see how it goes.

Concerning the Source API, thanks for your tip with Magnatune/Jamendo plugins, they seem to use it a lot and are good examples.

---

### Post by scrawl on 2010-05-07
Hi everyone,

I am happy to announce a very early version of the plugin. Currently it doesn't give many options, it just "works" (hopefully ;) )

Download here: [http://scrawl.bplaced.net/duplicate-source.tar.gz](http://scrawl.bplaced.net/duplicate-source.tar.gz)
To install, simply unzip to $HOME/.gnome2/rhythmbox/plugins (if folder not existing, create it)

Screenshot:
[IMG]http://scrawl.bplaced.net/duplicate-source.png[/IMG]

If you find any bugs or got further request, please tell me :p

Known issues:
 - When importing multiple files to the library at once, say 15, the plugin scans for duplicates 15 times 
 - Due to a limitation in Rhythmbox, you can't playback files from the duplicate source. However I plan to resolve this by creating a symlink to the file and using the symlink as file when adding the entry to the duplicate source

Current ToDo:
 - Configure dialog
 - Dont consider duplicate when the 2 tracks are from different albums
 - When one of the duplicates is from an album, and the other is from an "Unknown" album, consider the latter as duplicate
 - Rescan for duplicates when an entry gets removed from the library
 - Prefer files that have been added earlier when marking as duplicate

---

### Post by mihai.ile on 2010-05-08
Hello.
This is fantastic!

I am already working on the symlinks problem and I already got it working. just a little polish and I reply back with the solution.

---

### Post by mihai.ile on 2010-05-08
Ok, here it is the same plugin but now you can play the files in the duplicate list.

I also added a diff from your and my version to ease the integration.

Basically I create a hidden folder in ~/ with all symlinks and remove it at the exit (no need to have extra trash on people's filesystem as it is very easy and fast to recreate it next time; we need to search for duplicates again at startup so no big deal anyway)

---

### Post by mihai.ile on 2010-05-08
I also noted that the .rhythmbox-duplicates.ignore file grows with one byte every time you exit rhythmbox, better check it out before we grow into a 5GB .rhythmbox-duplicates.ignore file :D

---

### Post by scrawl on 2010-05-08
Thanks for your effort! I polished it up a bit so its now included. They were some problems though, the "Remove from library" and "Move to trash" didnt work anymore, because they relied on the location of the entry, but thats fixed now too. And by the way, the last bit is very much simpler than you did it: shutil.rmtree( os.path.expanduser("~/.rhythmbox-duplicates-symlinks/") ) and thats it ;)

So, lets call it version 0.2. Here is the full changelog:

 - Fixed: Due to a limitation in Rhythmbox, you can't playback files from the duplicate source
 - Fixed: .rhythmbox-duplicates.ignore file slowly increases its file size
 - Dont consider duplicate when the 2 tracks are from different albums
 - When one of the duplicates is from an album, and the other is from an "Unknown" album, consider the latter one as duplicate
 - Rescan for duplicates when an entry gets removed from the library
 - Prefer files that have been added earlier when marking as duplicate 


Download: [http://scrawl.bplaced.net/duplicate-source.tar.gz](http://scrawl.bplaced.net/duplicate-source.tar.gz)

---

### Post by mihai.ile on 2010-05-08
Yes, it's working good right now.
I was wondering if we need to create the path structure from the original file inside rhythmbox-duplicates-symlinks folder, because for example if I want to see the properties of the file, to see where is located, it's impossible to tell. Maybe we should make the exact path of the original file (including it's name) but just inside our rhythmbox-duplicates-symlinks folder, so if needed one can always have a clue from where in his music library that duplicate is coming from.

Oh and we have to figure out how we can get information about the original file... because sometimes you just need to liste/check properties of both original and the duplicate to decide which to remove.

Another thing... I think it's great not to have a menu entry, the plugin should just work, and now that is really fast in looking for duplicates, it could run in background, just like the missing files source. If there is a duplicate show the source, if not... hide it (oh and with this hide/show thing... I noticed that at startup the source appears, then right after dissapears to appear again a little after)

I think a that quite high quality functionality in rhythmbox is comming from this plugin :D

---

### Post by scrawl on 2010-05-08
> **mihai007 said:**
> 
I was wondering if we need to create the path structure from the original file inside rhythmbox-duplicates-symlinks folder, because for example if I want to see the properties of the file, to see where is located, it's impossible to tell. Maybe we should make the exact path of the original file (including it's name) but just inside our rhythmbox-duplicates-symlinks folder, so if needed one can always have a clue from where in his music library that duplicate is coming from.

The solution is much simpler: Don't show the properties dialog of the entry in the duplicate source, but of the entry in the library source. /Edit: patched, it works now.

> **mihai007 said:**
> 
Oh and we have to figure out how we can get information about the original file... because sometimes you just need to liste/check properties of both original and the duplicate to decide which to remove.

Yeah, I was thinking of this too, but I'm not sure how this should be implemented. A very simple solution would be a "Show versions" button that just switches to the library source and enters song name and artist into the search bar.

> **mihai007 said:**
> 
(oh and with this hide/show thing... I noticed that at startup the source appears, then right after dissapears to appear again a little after)

Well, it happens like this, first, I create the source (show), then I tell Rhythmbox to hide it when its empty (hide), then the source fills up (show). I have no idea what we could do about it, but thats very minor, isnt it :p

By the way, there was another bug coming with the playback thing, marking as non-duplicate didnt work properly, but I've fixed it. If anyone runs across that problem just download it again from here: [http://scrawl.bplaced.net/duplicate-source.tar.gz](http://scrawl.bplaced.net/duplicate-source.tar.gz)

And another thing, I will set up a launchpad page very soon where you can always get the latest source, submit code, view bugs, and translate the plugin (hooray!!).

---

### Post by Mr Nemo on 2010-05-08
Very cool, I'm trying this out now.

---

### Post by mihai.ile on 2010-05-08
Great, Do you think it would be acceptable to have an option for the plugin where you can check to show the original file in the duplicates list, next to its duplicates? this way we could have the original and it's duplicate(s) and you could easily choose to play all of them and remove the ones you don't want.

---

### Post by scrawl on 2010-05-08
Hey, thats actually a great idea :p I was really wondering how to implement that "show all versions" thingy, but this seems to be a very good solution.

---

### Post by Mr Nemo on 2010-05-08
How would I go about installing this? If its possible at this point.

---

### Post by mihai.ile on 2010-05-08
> **Mr Nemo said:**
> How would I go about installing this? If its possible at this point.

just download the archive provided in the earlier post and unpack it. Then you have to put the "duplicate-source" folder inside ~/.gnome2/rhythmbox/plugins/ folder. If it does not exist, create it.
Then, in rhythmbox just activate the plugin (Edit->Plugins)

After a little you should have a source called Duplicates (just like in the screenshots in this thread) if you actually have duplicated files in your library.

---

### Post by Mr Nemo on 2010-05-08
Thanks

---

### Post by Mr Nemo on 2010-05-08
Just installed it. Seems to work fine so far. Thanks guys, this is a good plugin.

---

### Post by Pifilatakanemu on 2010-05-09
Great news, this is something i desperately missed under linux players until now.

I'd love to see a feature to create a certain automatization in order to make it easier to handle large collections. 

MediaMonkey uses attributes like "last played, last added" etc. and automatically selects the duplicates on the base of these options and deletes them in one step.


I have no idea how hard it is to implement this feature, but it would certainly improve the handling for those with large collections and a lot of duplicates.

---

### Post by scrawl on 2010-05-09
> **flohmann said:**
> 
I'd love to see a feature to create a certain automatization in order to make it easier to handle large collections.

What do you mean? Some kind of automatic deletion when a duplicate is found? That shouldnt be hard to implement.

> 
MediaMonkey uses attributes like "last played, last added" etc. and automatically selects the duplicates on the base of these 

The plugin does this too, furthermore the order is like this
 * Quality
 * Album (Unknown Album -> duplicate)
 * Date added to library (added last is preferred)

---

### Post by scrawl on 2010-05-09
Here is a mockup for the preferences dialog, anything to add? (The Combobox has 2 entries, Remove from library and move to trash)

---

### Post by mihai.ile on 2010-05-09
for now, I think it would be sufficient.

---

### Post by mihai.ile on 2010-05-10
After some tests, it seems that the show/hide/show minor bug could be more relevant than we thought. Sometimes when I start rhythmbox the duplicates source neve appears even if I have the plugin enabled. Now my fear is that maybe the rhythmbox does things faster and somehow the order goes to show/show/hide and bum... never appears again until a restart of the plugin.

I don't know if it is possible not to show the duplicate source when activating the plugin, but only when the list has entries.

Of course I am not sure this is the real problem in the source not appearing though...

---

### Post by scrawl on 2010-05-10
> **mihai007 said:**
> After some tests, it seems that the show/hide/show minor bug could be more relevant than we thought. Sometimes when I start rhythmbox the duplicates source neve appears even if I have the plugin enabled. Now my fear is that maybe the rhythmbox does things faster and somehow the order goes to show/show/hide and bum... never appears again until a restart of the plugin.

Thats impossible, because I don't really tell Rhythmbox to hide it at that part, I just set the property "hide when empty". So even if the order gets scraped somehow, the source will always be visible when there are duplicates.

I will fix it anyway because that appearing and disappearing on startup bugs me.
> 
I don't know if it is possible not to show the duplicate source when activating the plugin, but only when the list has entries.

Yep, thats the solution.

---

### Post by Pifilatakanemu on 2010-05-10
> **scrawl said:**
> Here is a mockup for the preferences dialog, anything to add? (The Combobox has 2 entries, Remove from library and move to trash)


Looks very nice.

---

### Post by mihai.ile on 2010-05-10
Again, some things I discovered from using the plugin:

I noted that if you activate/deactivate the plugin several times, when you activate it, it shows the list of duplicates just fine, but then if I remove a file (move to trash in the music source) the list of duplicate files shows everything 2 or 3 times repeated, so the list of duplicate files... well duplicates the number of entries :)
I don't know if it has something to do with listeners...

---

### Post by scrawl on 2010-05-10
Thanks for pointing this out, it was indeed a problem with the listeners for entry-added / entry-deleted signals, they were not cleaned on deactivation. It's fixed in the bzr branch, which is, by the way, available at [https://code.launchpad.net/~scrawl/rb-duplicate-source/trunk](https://code.launchpad.net/~scrawl/rb-duplicate-source/trunk) so you can just type in bzr branch lp:rb-duplicate-source to always get the latest source code.

---

### Post by mihai.ile on 2010-05-11
Oh great so I can use Launchpad to submit any possible bugs/etc. It's easier to track and all.

---

### Post by mihai.ile on 2010-05-11
Oh.. I just noted that the project is not setup to use launchpad for bug tracking. can you check that?

Also, meanwhile just added a patch to fix the module name. Since now the plugin is rb-duplicate-source rhythmbox can't load the plugin if you get it from bzr.

---

### Post by scrawl on 2010-05-11
Preferences dialog is ready (and working!!!) :)

Download: [http://scrawl.bplaced.net/duplicate-source.tar.gz](http://scrawl.bplaced.net/duplicate-source.tar.gz)

> 
Also, meanwhile just added a patch to fix the module name. Since now the plugin is rb-duplicate-source rhythmbox can't load the plugin if you get it from bzr. 

The module name should still be duplicate-source, cause none of the rhythmbox plugins has this "rb" in front of it. The reason why this doesnt work in bzr is that I've called the project on launchpad rb-duplicate-source and now I can't rename the branch either :( So you have to rename it to duplicate-source when getting it from bzr, sorry.

> Oh.. I just noted that the project is not setup to use launchpad for bug tracking. can you check that?

[X]

---

### Post by The Real Dave on 2010-05-12
Great plugin, I downloaded the version in the comment above, and it lists duplicates perfectly. However, everytime I try to delete a file Rhythmbox crashes :(

EDIT: Ran it again, it first found 23 dupes, deleted them fine, though leaves a "Missing File". It then found ~1000 dupes, tried deleting at it got a Segmentation Fault

```
dave@system64:~$ rhythmbox

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/764
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

(rhythmbox:3753): RhythmDB-WARNING **: attempting to create entry that already exists: file:///home/dave/.rhythmbox-duplicates-symlinks/1090
Traceback (most recent call last):
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 318, in check_for_duplicates
    self.add_entry(entry_to_add, i)
  File "/home/dave/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 254, in add_entry
    self.db.set(new_entry, rhythmdb.PROP_ARTIST, self.db.entry_get(entry_to_add, rhythmdb.PROP_ARTIST))
TypeError: entry should be a RhythmDBEntry, is a void

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3753): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Segmentation fault
```

---

### Post by scrawl on 2010-05-12
Thats strange. Are you sure you are not trying to delete a file that doesnt exist anymore? Can you post the console output of rhythmbox -D duplicate-source when it crashes?

Additionally, commenting out lines 176 and 177 of __init__.py might help to localize the problem. (replace

```
			self.db.entry_move_to_trash( self.db.entry_lookup_by_location( location ) )
			self.db.entry_delete( entry )
```

with

```
			#self.db.entry_move_to_trash( self.db.entry_lookup_by_location( location ) )
			#self.db.entry_delete( entry )
```

and tell me if it still crashes then)


Edit: Those error messages should be fixed with this patch: replace line ~239 (new_entry = self.db.entry_new(self.entry_type, symlink_file_rb ) in __init__.py with 

```
			# Make sure the entry is not existing already
			if self.db.entry_lookup_by_location(symlink_file_rb) == None:
				new_entry = self.db.entry_new(self.entry_type, symlink_file_rb )
			else:
				return
```

---

### Post by mihai.ile on 2010-05-13
Hello.
I don't know if you are notified, but I submitted a patch with a bug I found on rev3 of the plugin in launchpad, not related to the above problem.

---

### Post by scrawl on 2010-05-13
Yes, I'm notified for bugs on launchpad. It seems your patch does the same as this one:

```
			# Make sure the entry is not existing already
			if self.db.entry_lookup_by_location(symlink_file_rb) == None:
				new_entry = self.db.entry_new(self.entry_type, symlink_file_rb )
			else:
				return
```

Can you try if this one also fixes your problem? Then I'll check it into bzr.

---

### Post by mihai.ile on 2010-05-13
yes, actually I tried avoiding return statements in the middle of the code/method, but yes, does the same, so as long as it's patched.. :D
EDIT: You can patch it, does the same.

---

### Post by scrawl on 2010-05-13
Latest version pushed to bzr. Changelog:

 - Fixed #579902 (Problem when using show bothh option and more than 2 duplicates)
 - Fixed #579911 (importing multiple files at once triggers duplicate check several times)
 - Also recognizes not 100% exact entries as duplicates by stripping common parts like "feat.", "vs.", "presents", "&", "and" ... (for example "A & B - Foo bar" and "A and B - Foo bar" will be recognized)
 - Before checking, the filters in the library source are resetted so we really get all entries in the source

---

### Post by mihai.ile on 2010-05-13
This is great, today is the day I actually used the plugin :D
Removed about 150MB of duplicates :D

Oh and to download directly from the launchpad, while in 

```
~/.gnome2/rhythmbox/plugins
```

just do:

```
bzr branch lp:rb-duplicate-source duplicate-source
```

---

### Post by The Real Dave on 2010-05-15
> **scrawl said:**
> Edit: Those error messages should be fixed with this patch: replace line ~239 (new_entry = self.db.entry_new(self.entry_type, symlink_file_rb ) in __init__.py with 

```
			# Make sure the entry is not existing already
			if self.db.entry_lookup_by_location(symlink_file_rb) == None:
				new_entry = self.db.entry_new(self.entry_type, symlink_file_rb )
			else:
				return
```

I edited the file, and ran Rhythmbox. Before I manually cleared out most of the duplicates (~2500), with the plugin enabled, Rhythmbox would just lock up. I later found out, after removing the duplicates by hand, that it's duplicating the duplicates. For example, I have one duplicate album at the moment, which the plugin has found almost 400 times. I've checked, and I definitely don't have 400 copies ;)

Though I don't exactly need this plugin anymore, I'll gladly help test new versions and that :)

---

### Post by scrawl on 2010-05-15
> **The Real Dave said:**
> I edited the file, and ran Rhythmbox.  I later found out, after removing the duplicates by hand, that it's duplicating the duplicates. For example, I have one duplicate album at the moment, which the plugin has found almost 400 times. I've checked, and I definitely don't have 400 copies ;)



This should be fixed in the newest release (- Fixed #579911 (importing / removing multiple files at once triggers duplicate check several times), did you already have that one or did you just edit the previous version?

---

### Post by CheshireMac on 2010-05-15
I'm actually having an issue regarding imports . . . when I imported my music to RhythmBox, all the files were duplicated in the library. I'm curious if there's a way to delete the duplicates without sifting through thousands of songs . . .

---

### Post by scrawl on 2010-05-15
Please try a newer version, its fixed there: [http://scrawl.bplaced.net/duplicate-source.tar.gz](http://scrawl.bplaced.net/duplicate-source.tar.gz)

---

### Post by The Real Dave on 2010-05-16
> **scrawl said:**
> This should be fixed in the newest release (- Fixed #579911 (importing / removing multiple files at once triggers duplicate check several times), did you already have that one or did you just edit the previous version?

Ah, my apologies, I had the previous version

---

### Post by Garthhh on 2010-05-19
> **mihai007 said:**
> just download the archive provided in the earlier post and unpack it. Then you have to put the "duplicate-source" folder inside ~/.gnome2/rhythmbox/plugins/ folder. If it does not exist, create it.
Then, in rhythmbox just activate the plugin (Edit->Plugins)

After a little you should have a source called Duplicates (just like in the screenshots in this thread) if you actually have duplicated files in your library.

Hi this look great
but I'm noob & having a bit of trouble installing
I downloaded the file from the 67th post
where do I find?
~/.gnome2/rhythmbox/plugins/ folder.



But don't see it in the list of plug ins on rhythm box

thanks for your hard work:)

---

### Post by mihai.ile on 2010-05-20
Ok, just start a terminal and use this command to install it:

```

wget http://scrawl.bplaced.net/duplicate-source.tar.gz -O tmp.tar.gz && mkdir -vp ~/.gnome2/rhythmbox/plugins/duplicate-source/ && tar -xf tmp.tar.gz -C ~/.gnome2/rhythmbox/plugins && rm -v tmp.tar.gz

```

What it does:
-download the plugin into tmp.tar.gz file
-create ~/.gnome2/rhythmbox/plugins/
-extract the plugin
-remove the downloaded tmp.tar.gz file

Then just restart Rhythmbox and check if you have it in the plugins list.

Hope it helps.

---

### Post by Garthhh on 2010-05-20
> **mihai007 said:**
> Ok, just start a terminal and use this command to install it:

```

wget http://scrawl.bplaced.net/duplicate-source.tar.gz -O tmp.tar.gz && mkdir -vp ~/.gnome2/rhythmbox/plugins/duplicate-source/ && tar -xf tmp.tar.gz -C ~/.gnome2/rhythmbox/plugins && rm -v tmp.tar.gz

```What it does:
-download the plugin into tmp.tar.gz file
-create ~/.gnome2/rhythmbox/plugins/
-extract the plugin
-remove the downloaded tmp.tar.gz file

Then just restart Rhythmbox and check if you have it in the plugins list.

Hope it helps.

That worked:)
I probably have several 1000's of duplicates
this will help me make a dent in them
some are a little trickier to find
same album, one just numbered tracks, or some with the track number in the title
sometimes I'll trade back up discs & basically have to pick through for what I don't have 
or suffer the consequences if I import en mass
it would be cool to set up queries with multiple rules
sort of a duplicate smart playlist

how would have I done the install through the GUI?

I also have music-applet-2.5.1 tar.gz  which is a lot like foxytunes I hope
I'm looking for onscreen controls with less clicks
stop me before I hyjack some more:P

---

### Post by scrawl on 2010-05-20
> **Garthhh said:**
> That worked:)
how would have I done the install through the GUI?

You can press Ctrl+H in the file manager, then you will see the hidden folders (including .gnome2 ), then you can navigate to .gnome2/rhythmbox/plugins or create the rhythmbox/plugins folders if they dont exist yet. Then you put the duplicate-source.tar.gz file in there and then right click on it -> unzip here.
> 
I also have music-applet-2.5.1 tar.gz  which is a lot like foxytunes I hope]

You can install panflute (formerly music-applet) through the package manager ;) Just kick in Synaptic and search for either music-applet or panflute, I don't know if its renamed yet in Karmic.

Then you can add it to the panel, by doing a right click on the panel -> add to panel.

---

### Post by Garthhh on 2010-05-20
I'm actually on Mint9
very similar The stock GUI is prettier & easier to understand

found it on synaptic as music applet 2.5.1
of course now I have to figure out how to make it work:)
I don't see it in the list of plugins?
I did stop & restart rhythm box
I can find the one I downloaded last night 
can't change the permissions to executable

---

### Post by scrawl on 2010-05-23
Hey guys,

I just uploaded a minor update. Changelog:
 - Duplicate check moved to the background so it doesn't block the UI
 - Stripped additional common strings before comparing (original mix, the, !, -, Ft)
 - Added a "sensitivity" option to the preferences window which determines how similiar 2 songs have to be when being considered a duplicate

Download here: [http://scrawl.bplaced.net/duplicate-source.tar.gz](http://scrawl.bplaced.net/duplicate-source.tar.gz) (or from bzr)

---

### Post by Garthhh on 2010-05-23
> **scrawl said:**
> Hey guys,

I just uploaded a minor update. Changelog:
 - Duplicate check moved to the background so it doesn't block the UI
 - Stripped additional common strings before comparing (original mix, the, !, -, Ft)
 - Added a "sensitivity" option to the preferences window which determines how similiar 2 songs have to be when being considered a duplicate

Download here: [http://scrawl.bplaced.net/duplicate-source.tar.gz](http://scrawl.bplaced.net/duplicate-source.tar.gz) (or from bzr)

Hi Scrawl,
I almost understand what to do with it
I've got the file downloaded & extracted
Now what?

I certainly have seen some strange behavior out of it 
I keep bumping into exact duplicates, that aren't found when I look at the entire library.
when I click on duplicate  I get 22 songs that I already deleted?
I probably don't understand how to use it or sumptin:)

---

### Post by kiwiot on 2010-06-12
Hi,

I went to download this plugin @ [http://scrawl.bplaced.net/duplicate-source.tar.gz ]("http://scrawl.bplaced.net/duplicate-source.tar.gz")

but keep getting a 403 forbidden error. Is this no longer available?[URL="http://scrawl.bplaced.net/duplicate-source.tar.gz"]
[/URL]

---

### Post by scrawl on 2010-06-12
Thats strange, I dont get the error. Can you try again?

---

### Post by kiwiot on 2010-06-13
Not sure either. 

I managed to download the file by setting up tunneling with firefox. Look like it is a problem to do with where I am connecting from (South Korea)

---

### Post by roundhay on 2010-06-23
> **scrawl said:**
> Here is a mockup for the preferences dialog, anything to add? (The Combobox has 2 entries, Remove from library and move to trash)

I would like to have the option in preferences to send duplicates to a 'Duplicates' folder instead of Delete Items.

With this option you would be able to switch duplicates at a later date if you found you had originally kept low quality version.

The user could set up a /home/user/Duplicates folder?

---

### Post by scrawl on 2010-06-24
> **roundhay said:**
> I would like to have the option in preferences to send duplicates to a 'Duplicates' folder instead of Delete Items.

With this option you would be able to switch duplicates at a later date if you found you had originally kept low quality version.

The user could set up a /home/user/Duplicates folder?

It's a good idea. Though there is no release of the plugin planned for the near future. I've added it to the ToDo list.

---

### Post by jnachtigall on 2010-06-30
I installed the plugins, but after activating it kills rhythmbox (but also does so after newstart, since it is still active). Here is the traceback:

```
Unhandled exception in thread started by <bound method DuplicatesRm.check_for_duplicates of <DuplicatesRm object at 0x887c7fc (RBPlugin at 0x84bda48)>>
Traceback (most recent call last):
  File "/home/jens/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 365, in check_for_duplicates
    if self.compare(entries[i], entries[i+1]) == True:
  File "/home/jens/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 240, in compare
    if string_match( self.strip_field(self.db.entry_get(entry1, rhythmdb.PROP_TITLE)), self.strip_field(self.db.entry_get(entry2, rhythmdb.PROP_TITLE)) ) >= sensitivity and string_match( self.strip_field(self.db.entry_get(entry1, rhythmdb.PROP_ARTIST)), self.strip_field(self.db.entry_get(entry2, rhythmdb.PROP_ARTIST))) >= sensitivity and ( string_match(self.strip_field(self.db.entry_get(entry1, rhythmdb.PROP_ALBUM)), self.strip_field(self.db.entry_get(entry2, rhythmdb.PROP_ALBUM))) >= sensitivity or (self.db.entry_get(entry1, rhythmdb.PROP_ALBUM) in self.unknown_translated) or (self.db.entry_get(entry2, rhythmdb.PROP_ALBUM) in self.unknown_translated) ):
  File "/home/jens/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 63, in string_match
    return float(intersection*2) / float(union)
ZeroDivisionError: float division
```Really a showstopper (especially since I was looking for such a tool for linux for several months already, and now there is, and then this :-( Maybe you can fix this?!

---

### Post by scrawl on 2010-06-30
Try to open __init__.py of the plugin and replace
```
return float(intersection*2) / float(union)
```
with
```

	if not float(union) == 0:
		return float(intersection*2) / float(union)
	else:
		return 0

```

I guess the reason why you get this is because you have songs with empty tags..

---

### Post by Robin-chan on 2010-08-05
I copied & pasted everything and installed the plugin, but whenever I try to select it in the Plugins window, Rhythmbox crashes. Is there maybe something I'm doing wrong?

Edit: I tried the above fix, but now it says "Unable to activate plugin Duplicate Source."

---

### Post by scrawl on 2010-08-06
Are you sure you typed everything in correctly? I've attached the modified file here. If it still doesn't work, start Rhythmbox in the console and post the output!

---

### Post by Robin-chan on 2010-08-06
```
** (rhythmbox:15253): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:15253): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:15253): Rhythmbox-WARNING **: Could not open device /dev/radio0
TypeError: Cannot create a consistent method resolution
order (MRO) for bases ImplementorIface, Orientable, Buildable
**
ERROR:/build/buildd/pygobject-2.18.0/gobject/pygobject.c:924:pygobject_new_full: assertion failed: (tp != NULL)
Aborted

```

---

### Post by scrawl on 2010-08-06
```
TypeError: Cannot create a consistent method resolution
order (MRO) for bases ImplementorIface, Orientable, Buildable
**

```
It's a bug in PyGTK or PyGObject, google it. As far as I know there is no fix at the moment.

---

### Post by Robin-chan on 2010-08-06
Seems like that bug has been around for a while... I wonder why no one has fixed it yet.

Thank you for clearing that up, though.

---

### Post by neresi on 2010-08-17
> **scrawl said:**
> You can press Ctrl+H in the file manager, then you will see the hidden folders (including .gnome2 ), then you can navigate to .gnome2/rhythmbox/plugins or create the rhythmbox/plugins folders if they dont exist yet. Then you put the duplicate-source.tar.gz file in there and then right click on it -> unzip here.

I did all that, but Rhythmbox does not show the plugin in its plugin list. The folder $HOME/.gnome2/rhythmbox/plugins had to be created first - the one with all the default Rhythmbox plugins is write-protected, so I can't just move the duplicate-source folder there. What else could I do? (Ubuntu 10.04 LTS - Lucid Lynx)

---

### Post by Leeteq on 2010-08-30
A duplicate finder would be great.

---

### Post by shaneburton on 2010-09-10
Ok totally off topic here, but I am having a heck of a time with Rhythmbox and plugins.  I have tried to add the plugin (and others) to the ~/.gnome2/rhythmbox/plugins directory and NONE of them are working.  

Any help would be greatly appreciated.

---

### Post by roswell1211 on 2010-10-17
Hi,
First of all - this looks great and thanks for putting in the effort to get it up and running correctly.
I have installed it and have a few minor problems (and 1 major one).
Firstly, when I restart Rhythmbox the 'Duplicates' list icon on the left never appears (I see earlier that it might not appear if the list is empty, but there are definitely duplicates as when I reactivate it in the plugins menu it shows up with some),
Secondly, how should I be using this - does it scan automatically? I have tried leaving it for hours and it only discovers 2 duplicates, one of which - as an example - is a song called 'Marie' by Steve Earle. I know for a fact that the whole album of 12 or 14 songs is duplicated in the same way but the other songs never show up. Am I doing something stupid? Do I need to tell it which files to scan or something?
And the major problem - as I understand it this should go through ID3 tags and find songs with duplicate titles/artists/albums is this correct?
As I have known duplicates, I don't know why it is not finding these - some of them may have different filenames or bitrates etc - but the tags are identical (as far as I can see). 
Again, though, despite all this, thanks for the work - I've tried using fdupes and fslint, but they don't even look at tags so can only find files that are identical in content (again, as far as I know).

Any help would be great.

---

### Post by kpsg25690 on 2010-10-21
Hi,i am new to rhythmbox and was looking for something like this.
i have similar problems as the previous post,
do you start it or does it work automatically?
nothing like "Duplicates" shows up in the side pane.

Could this have to do anything with maverick?

---

### Post by xieon on 2010-10-30
i installed the plugin, but I have no idea how to use it, could someone explain?

I activated the plugin, and restarted rhyhmbox, but I see no option for duplicates anywhere, I've played with the preferances, and have so many duplicates, however, nothing changes at all?

---

### Post by wilfgilbert on 2010-11-08
I have them same problem as above, anyone able to help?

---

### Post by KRL_UK on 2010-11-15
Same here.  The plugin sounds fantastic but I am afraid it is not working for me with Ubuntu 10.10.  The duplicates never show up in the side panel.

---

### Post by Tappir on 2010-11-26
There's a small, very fast python script to remove duplicates [here]("http://blog.tappir.com/?p=13")

---

### Post by .:Christopher:. on 2010-11-28
Well im really trying to switch to linux from windows  i really like it so far but and getting a little frustrated with this one and could use some help. ive Googled my bum off and still no prevail.

it shows up as duplicate source under plugins and i saw it on the left pain once! but was not able to use it.  not i can not get it back on that pain but it remains in the plugin list and it is checked off.

any help would be greatly appreciated.

---

### Post by mvik on 2010-12-04
hii .. 
i am trying to download the file from ur website .. but am unable to do so .. can you attach it or something .. ( i am downloading from Taiwan .. )

---

### Post by wwuster on 2010-12-20
I converted the script in Tappir's post #98 of this tread to actually move the duplicate mp3s to a temporary directory. Since I don't do python I did it in php. I found that about 10% of my mp3s were duplicates. This just moves them to .../Desktop/tmp from the source directory .../Desktop/mp3, in my case. Make sure that the destination directory for the duplicates exists,
or modify this script to create it if it doesn't. I then deleted the duplicates from the temporary directory after I was confident that the script did what I expected. I gained about 10 gigs of disk space by removing duplicates.

William

<?php


$db = "/home/bill/.local/share/rhythmbox/rhythmdb.xml";

$doc = new DOMDocument();
$doc->load( $db );

$entries = $doc->getElementsByTagName( "entry" );

$cnt = 0;
$songs = array();

foreach( $entries as $e )  {
   $type = $e->getAttribute("type");
   if ($type=="ignore")  {
   	continue;
   }
   else if ($type=="lastfm-station")  {
   	continue;
   }
   else if ($type != 'song')  {
   	continue;
   }

   $artist = $e->getElementsByTagName("artist")->item(0)->textContent;
   $title = $e->getElementsByTagName("title")->item(0)->textContent;
   $album = $e->getElementsByTagName("album")->item(0)->textContent;
   $duration = (int)$e->getElementsByTagName("duration")->item(0)->nodeValue;
   $location = urldecode($e->getElementsByTagName("location")->item(0)->textContent);

   $flag = false;

   foreach ($songs as $s)  {
   	$tdif = abs($duration - $s["duration"]);
   	if (
   			$title == $s["title"] &&
   			$artist == $s["artist"] &&
   			($tdif < 2 || $album == $s["album"])

   		)  {
   		printf("%s\n", $location );
   		$location = str_replace("file:///home/bill/Desktop/mp3/", "", $location);
   		$cmd = "mv \"/home/bill/Desktop/mp3/$location\" \"/home/bill/Desktop/tmp/$location\"";
   		system($cmd);
   		$flag = true;
   		break;
   	}
   }

   if ($flag)  {
   	continue;
   }


   $a = array();
   $a['title'] = $title;
   $a['artist'] = $artist;
   $a['duration'] = $duration;
   $a['album'] = $album;
   $a['location'] = $location;             // just to see the original

   array_push($songs, $a);

   $cnt++;
   printf("%d\n", $cnt);

}
?>

---

### Post by pbhill on 2010-12-21
I've tried the plug in developed by Scrawl and mihai007. Seems to work quite well! Thanks for all that work!

Thanks to this duplicate finder, I have discovered a problem with my music library. Something (some app) is constantly rearranging my files and folders! I keep my music in folders "Artist>Album>Tracks". I'm finding duplicate tracks being created with a separate folder for each album. "Artist-Album>Tracks"
I use Banshee as a rule. Rhythmbox has always been there in the background and never caused any problems. I recently tried Media Monkey in a Windows VM. Do you suppose Media Monkey is rearranging my library in the background?

---

### Post by pbhill on 2010-12-26
> **pbhill said:**
> I've tried the plug in developed by Scrawl and mihai007. Seems to work quite well! Thanks for all that work!


Well, it worked once but not again. I don't see any duplicate file in the sidepane now. Is there some way to start/stop this script?

---

### Post by Tappir on 2010-12-30
So scrawl has stopped maintaining this plugin and it no longer works?

If so, I may consider creating a similar (working) GUI solution

> **wwuster said:**
> I converted the script in Tappir's [post #98]("http://art.ubuntuforums.org/showpost.php?p=10166680&postcount=98") of this tread to actually move the duplicate mp3s to a temporary directory. Since I don't do python I did it in php. I found that about 10% of my mp3s were duplicates. This just moves them to .../Desktop/tmp from the source directory .../Desktop/mp3, in my case. Make sure that the destination directory for the duplicates exists,
or modify this script to create it if it doesn't. I then deleted the duplicates from the temporary directory after I was confident that the script did what I expected. I gained about 10 gigs of disk space by removing duplicates.

William

<?php
.. 
       if (
               $title == $s["title"] &&
               $artist == $s["artist"] &&
               ($tdif < 2 || $album == $s["album"])
          ..
}
?>

Useful script :-) 
*$tdif < 2* should be* in_array($tdif, range(-1,1))* if you want the same behaviour as the original, where the difference allowed is either -1 second, 0 second (same duration), or +1 second.

For example, if:
Track A = 10 seconds
Track B = 9 seconds

Depending which track appears first in the xml file, it will either calculate as:

Track A - Track B = 1
or
Track B - Track A = -1

By the way, does it preserve the directory structure when moving duplicates?
If not, it'd be a cool idea to generate a bash script with 'rm' commands on the desktop instead.
Then you could still choose whether or not to run it (deleting the files), and edit it to choose which files to delete etc.
The benefit would be not having to remember which directories duplicates should be moved back to :-D

I've just realized Banshee is the default music player in the upcoming natty, which also suffers from no detection of duplicate tracks (and no extension to fix it). So i'll divert interest in creating an extension to that from rhythmbox.

Banshee looks better than Rhythmbox in every way, except it doesn't automatically group an album by various artists into a single album entry (maybe i'll write an extension for this too? :-D).

---

### Post by linuxopjemac on 2011-06-03
mihai007: thanks for your script, it works great!

---

### Post by thogz11 on 2011-08-08
Got the same problem. Tappir's link (python script) doesn't work for me. I followed the instructions correctly, still, the dupes goes back again.. :( sorry guys I'm just a newbie linux user..

---

### Post by emyr42 on 2011-08-21
```
emyr@emyr-desktop:~$ rhythmbox

(rhythmbox:4082): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Traceback (most recent call last):
  File "/home/emyr/.gnome2/rhythmbox/plugins/duplicate-source/__init__.py", line 88, in activate
    self.entry_type = self.db.entry_register_type("DuplicateEntryType")
AttributeError: '__main__.RhythmDBTree' object has no attribute 'entry_register_type'

(rhythmbox:4082): GLib-GObject-CRITICAL **: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed

(rhythmbox:4082): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

This is what I see if I launch from terminal, no Duplicates Source appears in the sidebar. Don't know Ruby yet, so I'm in no position to work on this.

---

### Post by ryurage on 2012-03-26
Using 11.10 and being aware that the local plugins directory for Rhythmbox at this time is ~/.local/share/rhythmbox/plugins, I cannot figure out how to get the plugin to show up in the list of plugins to edit.  Any suggestions?

---

### Post by j4mb4l4j4 on 2012-08-22
me neither, I have some plugins in that folder but couldn't figure out how to activate them. Is there maybe a permission problem ?

---

### Post by davidmohammed on 2012-08-22
any plugin with a .rb-plugin extension will not work in newer v2.9x versions of rhythmbox.

These will need to be recoded to be GTK3+ compatible.

---

### Post by xDeja on 2013-05-24
Has anybody modified this to work with GTK3+? The only thing I could think to change was renaming the .rb-plugin extension to .plugin and changing the IAge field in the .plugin file to 2. But that didn't work... 

[This]("https://live.gnome.org/RhythmboxPlugins/WritingGuide") is what I was using as a reference but I am afraid that most of it is a little beyond me. It is hard to believe that Rhythmbox doesn't have a delete duplicates plugin by default.

---

