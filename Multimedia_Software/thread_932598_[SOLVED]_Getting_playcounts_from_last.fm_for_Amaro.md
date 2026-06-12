---
title: "[SOLVED] Getting playcounts from last.fm for Amarok"
date: 2008-09-28
forum: Multimedia Software
---

### Post by nirpius on 2008-09-28
I recently buggered up a new install and so have lost most of my Amarok database. This caused me to do some research into a way to get my playcount out of last.fm. I found a ruby script on kde.apps that can do this. Here is the URL:

[http://kde-apps.org/content/show.php/Last+Sync?content=65784](http://kde-apps.org/content/show.php/Last+Sync?content=65784)

And for those of you who want to know what it contains, below is a copy of what I saw when I opened it with gedit:

```
#
# Lastsync - Syncs last.fm charts to your Amarok
#
# Copyright (2007):
# - Kevin Bocksrocker < kevin.bocksrocker@gmail.com >
#
# This file may be used under the terms of the GNU General Public License
# version 2.0 as published by the Free Software Foundation and appearing in
# the file LICENSE included in the packaging of this file.
#
# This file is provided AS IS with NO WARRANTY OF ANY KIND, INCLUDING THE
# WARRANTY OF DESIGN, MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE

require 'sqlite3'

require 'song'

class Amarok

# Prepare the Amarok database
def initialize(path)
	@db = SQLite3::Database.new(path)
	@db.execute("DELETE FROM statistics")
end

def getURL(artist, name)

	if artist == nil or name == nil
		return nil
	end

	resultArtist = @db.get_first_row("SELECT * FROM artist WHERE LOWER(name) = \"#{artist.downcase}\"")
	if resultArtist == nil
		puts "WARNING: No entry for artist '#{artist}'"
		return nil
	end

	result = @db.get_first_row("SELECT * FROM tags WHERE artist = \"#{resultArtist[0]}\" AND LOWER(title) = \"#{name.downcase}\"")
	if result == nil
		puts "WARNING: No entry for song '#{artist}' - '#{name}'"
		return nil
	end

	return result[0]

end

def getDeviceID(url)

	if url == nil
		return nil
	end

	result = @db.get_first_row("SELECT * FROM tags WHERE url = \"#{url}\"")
	if result == nil
		return 0
	end

	return result[20].to_i

end

def getUID(url)

	if url == nil
		return nil
	end

	result = @db.get_first_row("SELECT * FROM uniqueid WHERE url = \"#{url}\"")
	if result == nil
		return 0
	end

	return result[2]

end

def getScore(url)

	if url == nil
		return nil
	end

	result = @db.get_first_row("SELECT * FROM statistics WHERE url = \"#{url}\"")
	if result == nil
		return 0
	end

	return result[4].to_f

end

def getPlaycount(url)

	if url == nil
		return nil
	end

	result = @db.get_first_row("SELECT * FROM statistics WHERE url = \"#{url}\"")
	if result == nil
		return 0
	end

	return result[6].to_i

end

def getLastPlay(url)

	if url == nil
		return nil
	end

	result = @db.get_first_row("SELECT * FROM statistics WHERE url = \"#{url}\"")
	if result == nil
		return 0
	end

	return result[3].to_i

end

def getFirstPlay(url)

	if url == nil
		return nil
	end

	result = @db.get_first_row("SELECT * FROM statistics WHERE url = \"#{url}\"")
	if result == nil
		return 0
	end

	return result[2].to_i

end

def update(song)

	# Get URL
	song.url = getURL(song.artist, song.name)
	if song.url == nil
		return nil
	end

	# Get Unique ID and Device ID
	song.uniqueid = getUID(song.url)
	song.deviceid = getDeviceID(song.url)

	firstplay = getFirstPlay(song.url)
	if firstplay != 0 and firstplay < song.firstplay
		song.firstplay = firstplay
	end

	lastplay = getLastPlay(song.url)
	if lastplay != 0 and lastplay > song.lastplay
		song.lastplay = lastplay
	end

	playcount = getPlaycount(song.url)
	song.score = getScore(song.url)
	song.playcount.times do |i|
		if( (playcount + i) <= 0 )
			song.score = 50
		else
			oldscore = song.score
			song.score = (( oldscore * (playcount + i)) + 100) / ((playcount + i) + 1)
		end
	end
	song.playcount += playcount


	if @db.get_first_row("SELECT * FROM statistics WHERE url = \"#{song.url}\"") == nil
		@db.execute("INSERT INTO statistics VALUES(\"#{song.url}\", #{song.deviceid}, #{song.firstplay}, #{song.lastplay}, #{song.score}, 0, #{song.playcount}, \"#{song.uniqueid}\", 0)")
	else
		@db.execute("UPDATE statistics SET createdate=#{song.firstplay}, accessdate=#{song.lastplay}, percentage=#{song.score}, playcounter=#{song.playcount} WHERE url = \"#{song.url}\"")
	end

end

end
```

I unpacked it to this directory:

/home/My_username/.kde/share/apps/amarok/scripts

then ran it with this command:

~/.kde/share/apps/amarok/scripts/lastsync$ ./lastsync.rb nirpius

where nirpius is my last.fm username but was given this error message:

```
./amarok.rb:14:in `require': no such file to load -- sqlite3 (LoadError)
	from ./amarok.rb:14
	from ./lastsync.rb:18:in `require'
	from ./lastsync.rb:18

```

I did this as per some instructions I found on a discussion page on the last.fm website:

[http://www.last.fm/group/Amarok+Users/forum/18538/_/454099](http://www.last.fm/group/Amarok+Users/forum/18538/_/454099)

***

That is all the info. I can provide atm but if you need anything else, please let me know and if you are any good at patching up Ruby codes, then I'm sure the author of this script would want your input, there's a link on the kde.apps page.

Any help at all as to what is meant by my error message or how to resolve this even better :D

Thank you wonderful Ubuntu community.

---

### Post by nirpius on 2008-09-28
I'm a fool, I just needed to install libsqlite3-ruby

Ah well

---

