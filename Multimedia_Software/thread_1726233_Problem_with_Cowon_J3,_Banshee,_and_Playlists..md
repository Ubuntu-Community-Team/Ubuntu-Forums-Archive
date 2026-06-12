---
title: "Problem with Cowon J3, Banshee, and Playlists."
date: 2011-04-10
forum: Multimedia Software
---

### Post by clappboard on 2011-04-10
So, I have recently bought a  Cowon J3.  It's great, except playlists.  Whenever I sync it, the  playlists, copy over fine, but on the device it just says no file.  I  read somewhere about a script that would convert the paths in the *.m3u  to the correct format, and change the UNIX-style slashes to DOS-style  slashes.  Apparently I just drop it in the /Music directory, make it  executable, then run it to convert the playlists.  However, the J3 is a flash FAT32 filesystem, which does not support creating executable files.  So I took the script, and edited so it could sit on my desktop instead of on the device itself, but it's still not working.
I've included the original file and my edited one:


Original:

# Convert Unix m3u files created by banshee, mpd, and other music managers 
#   into a format that the Cowon S9/J3 can understand. 
# 
# Original Script by (c) 2009 James Ogley [http://jamesthevicar.com](http://jamesthevicar.com) 
# 
# Place this script in the MUSIC directory of the S9/J3, where the M3U playlists 
# should be. 
# This version uses tofrodos. 

# Change paths to absolute paths
sed -i '/^[^#]/ s?^?/Music/?' *.m3u 
# Convert all UNIX slashes to DOS backslashes 
sed -i '/^\// s/\//\\/g' *.m3u 
# Convert Unix line endings to DOS line endings 
todos -uo *.m3u 


...and mine:

# Convert Unix m3u files created by banshee, mpd, and other music managers 
#   into a format that the Cowon S9/J3 can understand. 
# 
# Original Script by (c) 2009 James Ogley [http://jamesthevicar.com](http://jamesthevicar.com) 
# 
# Place this script in the MUSIC directory of the S9/J3, where the M3U playlists 
# should be. 
# This version uses tofrodos. 

# Change directory to the Music folder on the device
cd /media/3B4C-61A5/Music/
# Change paths to absolute paths
sed -i '/^[^#]/ s?^?/Music/?' *.m3u 
# Convert all UNIX slashes to DOS backslashes 
sed -i '/^\// s/\//\\/g' *.m3u 
# Convert Unix line endings to DOS line endings 
todos -uo *.m3u 


Thanks in advance.

---

