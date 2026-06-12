---
title: "Rythmbox Sandisk Clip Zip Playlist Support"
date: 2014-08-12
forum: Multimedia Software
---

### Post by Floyd_Wallace on 2014-08-12
I need help. On Xubuntu 12.10, Rhythmbox (version 2.95) worked perfectly with my Sandisk Clip Zip and could create playlists (m3u) with no problem. The player itself is in MSC mode, I use rsync to copy files over from my Music Library.

Well, Rhythmbox 3.02 (my version on Xubuntu 14.04 (AMD64) does not support playlists anymore. 

Yes I've created the .is_media_player file, and Rhythmbox can SEE the player and read the contents of the music folders (I have my files on the extra 32 GB card, that's a sweet feature of this Linux Friendly ... at least until Rhythmbox devs screwed everything up ... media player). 

I CANNOT however click the rightwards triangle and see the already (about 15) existing playlists I'm using on the player (that again, were created just fine in Rhythmbox 2.95). I'd like to downgrade, but don't look forward to spending five days hunting around for this library and that which configure complains is not there -- my time on my computer is very limited, and what there is often is behind a stupid firewall.

I can import the playlists, but the names only show up. There are no songs on the playlists. Though they work fine on my player.

Here's an example playlist which works find on my player but shows up empty in the New, less-improved, feature removed, Rhythmbox:

File: Plimsouls.m3u

```
#EXTM3U 
#EXTINF:,Shaky City 
MUSIC\MUSIC\The Plimsouls\Everywhere At Once\01 Shaky City.mp3 
#EXTINF:,Magic Touch 
MUSIC\MUSIC\The Plimsouls\Everywhere At Once\02 Magic Touch.mp3 
#EXTINF:,Oldest Story In The World 
MUSIC\MUSIC\The Plimsouls\Everywhere At Once\03 Oldest Story In The World.mp3 
#EXTINF:,Lie, Beg, Borrow and Steal 
MUSIC\MUSIC\The Plimsouls\Everywhere At Once\04 Lie, Beg, Borrow and Steal.mp3 
#EXTINF:,Play the Breaks 
MUSIC\MUSIC\The Plimsouls\Everywhere At Once\05 Play the Breaks.mp3 
```

FWIW, both Exaile and Clementine CAN read the playlists on the player, and CAN write (broken) playlists on them -- I have to use SCITE to search/replace the forward slash (/) with a windows-friendly backwards slash (\). If I HAVE TO I can use these media players to manage my playlists, if I get very industrious I will write a Ruby script that cleans the playlists up. 

But I'm thinking -- the Rhythmbox Devs can't be that dumb/evil to take away simple MSC class external playlists can they?

I'm looking for what I had before, the ability of Rhythmbox to create playlists on the player the way Itunes does on Ipods, either with someone pointing me to a downgrade deb file, or some way to configure hidden stuff in Rhythmbox 3.02.

Any help would be appreciated. You can't believe how much time I've already burned on this, just to get playlists working (and no, icky Easy Tag is not a solution, I don't fancy using Emacs to move lines up and down -- something like the drag/drop ability of Itunes with Ipods is what I HAD with the old Rhythmbox and what I want now).

ETA: I've read on Ask Ubuntu that Clementine supposedly has the ability to write DOS path file playlists, but cannot find it. My version of Clementine is 1.2. I will also if I write the Ruby Code post it here. I like Ruby (a lot more than Shell/Bash code) and heck, Ruby is just fun. But I'd really like an all in one solution.

---

### Post by Floyd_Wallace on 2014-08-27
I'm going to reply to my own thread, because I found some answers and wrote a little script in Ruby to fix that last inch of getting playlists working in this player.

First, the latest version of Rhythmbox does not support exporting playlists to the San Disk Clip Zip player. For whatever reason, it just does not. The previous, v. 2.95 release with Xubuntu 12.10 worked fine, this version with Xubuntu 14.04 does not.

Solution?

Clementine for the music on my computer, which by the way is a very nice music player, and Exaile for managing playlists on the San Disk Clip Zip plus. 

Exaile allows you to replace the music library files with a new directory. Very handy if you've updated or changed your files on your player. You can create playlists based on the files ON THE PLAYER, and then export them.

However, the files contain ../ and / which don't work. The ../ needs to be removed and the / separators changed to DOS \ separators.

I have created a Sourceforge project that contains the Ruby 1.9 script that fixes the exported playlists.

You can download it here: [https://sourceforge.net/projects/fixplaylist/](https://sourceforge.net/projects/fixplaylist/)

Obviously, you need both Exaile and Ruby 1.9, both of which are available in the Xubuntu 14.04 repositories.

Then, download the .rb file, change the permissions to ugo+x and copy the file to your path such as: 

```

chown ugo+x fix_playlist.rb
sudo cp fix_playlist.rb /usr/local/bin

```

And you have an easy utility that searches the supplied directory on the command line and fixes all the .m3u playlist files. If the directory contains no such files the program exits, and if the program has no directory supplied on the command line or is invoked with:

```

fix_playlist.rb --help

```

You will get the help printed out. 

The script is very easy to use, hope it provides some use to those in the Ubuntu Community.

A few other things.

First, Podcasts will not play in a playlist if the Genre ID3 tag is set to "Podcast" (so set it to something else) OR if it is in the Podcast folder. This is a firmware design choice by the engineers at San Disk because users were complaining that "Play All" music would include Podcasts.

Second, you can also edit the .m3u files by hand using Xemacs or ScITE if you like. Using search and replace just eliminate the starting ../ and replace the / with a \ character.

Third, if you don't like Exaile you can use Easy Tag to create playlists, see here: [http://forums.sandisk.com/t5/Sansa-Clip-Sansa-Clip/HOWTO-Creating-m3u-Playlists-using-easyTAG-on-Linux/td-p/33500](http://forums.sandisk.com/t5/Sansa-Clip-Sansa-Clip/HOWTO-Creating-m3u-Playlists-using-easyTAG-on-Linux/td-p/33500). Beware of course that the file you get cannot be dragged/dropped in order, you must old-fashioned copy-paste lines around to change the order with a Text Editor like ScITE or Xemacs.

Hope this helps someone.

---

### Post by bvmarshall-99 on 2014-09-01
Floyd - thank you for this. Ran into this exact problem on upgrade from Ubuntu 12.04 to 14.04. So, now at least I know it's a Rhythmbox issue. Really odd they dumped that feature. Going to try your Exaile approach.

---

