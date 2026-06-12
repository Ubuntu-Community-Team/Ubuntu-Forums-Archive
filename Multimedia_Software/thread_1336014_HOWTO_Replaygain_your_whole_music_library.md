---
title: "HOWTO: Replaygain your whole music library"
date: 2009-11-24
forum: Multimedia Software
---

### Post by Darwin Award Winner on 2009-11-24
If you're looking for a way to add replay gain tags to all of your music all at once, especially if your music collection consists of multiple file formats, this HOWTO will describe two ways to do it.

The first way is to use a program called Quod Libet (or its companion, Ex Falso). *Recent* versions of these programs feature an extension that can apply replaygain to large sets of files at once. However, the version in Jaunty is not recent enough to include this feature, and I don't think the version in Karmic is either. (Apparently, you can also use Foobar2000 in wine, but I haven't tried that.)

The second way is to use my script. I have a music collection in at least four different formats (mp3, ogg, flac, wavpack, maybe a handful of aac) and multiple sample rates, so I wrote this one script to replaygain them all. The script assumes that each directory is an album (for the purposes of album gain values), and it walks the whole directory tree starting from where you tell it. In each folder, it searches for every kind of music file that it knows about, and applies replay gain to all the ones that it finds. If it doesn't support your music format of choice, you can add it with two lines of code.

I have written a script to add replaygain tags to an entire collection of music files at once. I use it to apply replaygain to my whole music collection, or to any new files/albums I add to it. When run, the script will search recursively through an entire folder and all of its subfolders and will add replaygain data to all the music files of any known file type that it finds. The script assumes that each folder represents an album (for the purposes of calculating album gain).

To use it, copy the text below into a script called "gain-music-dir-recursive.sh" (or whatever you want to call it), and run it something like this:

$ gain-music-dir-recursive.sh ~/Music/ ~/Podcasts/

Then go and wait a while if you have a large music collection. (Or sit and watch the text scroll by for a while. It can be mesmerizing.) You can supply any number of directories on the command line, and it will process each of those directories and all of their subdirectories. If you don't supply any directory names, it will process the current directory.

Note that you will need to install the replaygain tool for each file type in your music library. To determine the correct program, look here: [http://wiki.hydrogenaudio.org/index.php?title=Replay_Gain]("http://wiki.hydrogenaudio.org/index.php?title=Replay_Gain"). However, you will then need to figure out which package contains the tool and install that package.

Anyway, here's the script:

```
#!/bin/bash

# gain-music-dir-recursive.sh: A script to apply replaygain to an
# entire directory tree (or several).

# Usage: gain-music-dir-recursive.sh [paths...]
# Supply one or more paths in which to apply replaygain to all music files.

# This determines what the script does when run with no arguments
DEFAULT_MUSIC_DIR="." # You can set this to your music folder

if [ -z "$(echo $@)" ]; then
  set $DEFAULT_MUSIC_DIR
fi

record_error () {
  errors="$errors\n$@"
}

print_errors () {
  if [ -n "$errors" ]; then
    echo -ne "The following errors were encountered: $errors\n"
  fi
}

gain_general_single () {
  if [ -z "$1$2" ]; then
    echo "Invalid input: $@"
    return
  fi

  local gain_target_file="$1"
  if [ "$(echo *.$gain_extension)" = "*.$gain_extension" ]; then
    #echo "No $gain_extension files in $(pwd)."
    return
  fi

  local gain_command="$2"
  local gain_track_opt="$3"

  local gain_opt="$gain_track_opt"

  echo "Running $gain_command $gain_opt \"$gain_target_file\" in $(pwd)"
  $gain_command $gain_opt "$gain_target_file" || record_error "In $(pwd):\n  Failed to run: $gain_command $gain_opt \"$gain_target_file\".\n  This file was not gained."
}

test_executable () {
  if which $(echo $1 | sed -e 's/ .*//') &>/dev/null; then
    return 0; #true
  else
    return 1; #false
  fi
}

gain_general () {
  if [ -z "$1$2" ]; then
    echo "Invalid input: $@"
    return
  fi

  local gain_extension=$1
  if [ "$(echo *.$gain_extension)" = "*.$gain_extension" ]; then
    #echo "No $gain_extension files in $(pwd)."
    return
  fi

  local gain_command=$2
  local gain_track_opt=$3
  local gain_album_opt=$4

  # Test for executability of the replaygain program
  test_executable $gain_command || {
    record_error "Unable to gain $gain_extension files because $(echo $gain_command | sed -e 's/ .*//') is not installed.";
    return;
  }

  local gain_opt="$gain_track_opt"
  if [ -f "ALBUMGAIN" ]; then
    local gain_opt="$gain_album_opt"
  fi

  echo "Running $gain_command $gain_opt *.$gain_extension in $(pwd)"
  $gain_command $gain_opt *.$gain_extension || {
    record_error "In $(pwd):\n  Failed to run: $gain_command $gain_opt *.$gain_extension\n  Falling back to one-track-at-a-time replaygain.";
    shift;
    local target;
    for target in *.$gain_extension; do
      gain_general_single "$target" "$@";
    done
  };
}

# These
gain_mp3 () {
  gain_general mp3 "mp3gain -k -p" "-r" "-a";
}

gain_ogg () {
  gain_general ogg "vorbisgain -a -s";
}

gain_flac () {
  gain_general flac "metaflac --add-replay-gain --preserve-modtime";
}

gain_wv () {
  gain_general wv "wvgain -a";
}

gain_aac () {
  gain_general aac "aacgain -k -p" "-r" "-a";
  gain_general mp4 "aacgain -k -p" "-r" "-a";
}



gain_dir () {
  echo "Adding replaygain to known file types in $(pwd)"
  gain_mp3
  gain_ogg
  gain_flac
  gain_wv
  gain_aac
  echo "Finished adding replaygain in $(pwd)"
}

gain_dir_recursive () {
  gain_dir
  if [ "$(echo */)" != "*/" ]; then
    local dir
    for dir in */; do
      pushd "$dir";
      gain_dir_recursive
      popd;
    done
  fi
}

for dir in "$@"; do
  pushd "$dir"
  gain_dir_recursive
  popd;
done

print_errors
```

Update: I also have a second script for doing the same thing. However, this script requires Gstreamer and Quod Libet, so if you don't want to install those, then stick with the script in this post. If you want the newer and arguably better script, go to [https://github.com/DarwinAwardWinner/rganalysis](https://github.com/DarwinAwardWinner/rganalysis)

---

### Post by starpause on 2010-07-29
thank you for the cool script, i've been using it! 

i have one question. when you do an aacgain, you're using both the -a flag "apply Album gain automatically" as well as the -r flag "apply Track gain automatically", two features that specify opposite behavior. so it seems to me either -a or -r should be specified but not both. 

perhaps i'm either misunderstanding aacgain or your script, so please shed some light on me :KS

---

### Post by Darwin Award Winner on 2010-07-29
If you manage to work your way through the gain_general function, you'll see that it selects only one of either track or album gain, not both. Basically, it always does per-track gain unless the folder contains a file called "ALBUMGAIN". This is the relevant bit of code:

```

local gain_opt="$gain_track_opt"
if [ -f "ALBUMGAIN" ]; then
  local gain_opt="$gain_album_opt"
fi
```

---

### Post by StrikerNL on 2010-07-30
This seems to work really well, it's going now for an odd 200 GB of generally MP3s.

Now when this is run for a second time (e.g. music added to collection), will this skip the ones already processed?

---

### Post by Darwin Award Winner on 2010-07-30
> **StrikerNL said:**
> Now when this is run for a second time (e.g. music added to collection), will this skip the ones already processed?

That depends on the behavior of the individual format-specific replaygain tools. For example, mp3gain never needs to recalculate replaygain. I believe most of them do not need to recalculate.

---

### Post by Darwin Award Winner on 2010-09-25
Here is another script to do the same thing, only using Gstreamer. It also required quodlibet to be installed, because it uses quodlibet's awesome tagging tools to write the replaygain tags. I am posting this in addition to the original bash script instead of replacing it, because the bash script has had more testing and has no dependency on quodlibet. However, this script has several advantages over the original:

[LIST]
[*]It uses gstreamer, so it automatically supports all formats that gstreamer supports
[*]It will definitely not rescan files unless necessary
[*]It does not require you to find and install the correct replaygain tool for each music format in your music library.
[/LIST]

Edit: The code is now on GitHub: [https://github.com/DarwinAwardWinner/rganalysis](https://github.com/DarwinAwardWinner/rganalysis)

---

### Post by dartmusic on 2011-01-25
Two questions; first, has anyone tried the Quod Libet script?  Second, how do you invoke the Quod Libet script?

Thanks!

---

### Post by Darwin Award Winner on 2011-01-25
I already use my script on my own library, since this is why I originally wrote it. It works for me. Secondly, I have since moved the code to GitHub, where you can always find the latest version. The GitHub Repository also shows the help text of the script.

If you aren't familiar with running scripts on the command line, it's probably easier just to use Quod Libet istelf. It does a perfectly fine job, and the only reason I wrote the script was that I wanted to automate it.

---

### Post by dartmusic on 2011-01-26
> **Darwin Award Winner said:**
> I already use my script on my own library, since this is why I originally wrote it. It works for me. Secondly, I have since moved the code to GitHub, where you can always find the latest version. The GitHub Repository also shows the help text of the script.

If you aren't familiar with running scripts on the command line, it's probably easier just to use Quod Libet istelf. It does a perfectly fine job, and the only reason I wrote the script was that I wanted to automate it.

I'm completely familiar with running scripts from the command line.  I was asking about the Quod Libet script.  I don't understand how to use that.  If you wouldn't mind walking me through it, I would appreciate it.

Thanks!

---

### Post by Darwin Award Winner on 2011-01-26
I've added a --dry_run option to the script, so now you can test it without worrying about destroying your files. 

Anyway, download it from GitHub, put it in your $PATH, and run it with your music directory as an argument:

```
$ rganalysis.py $HOME/Music/
```

The download link for the script itself is here: [https://github.com/DarwinAwardWinner/rganalysis/raw/master/rganalysis.py](https://github.com/DarwinAwardWinner/rganalysis/raw/master/rganalysis.py)

Oh, and you'll need to install some python modules, I suppose.

---

### Post by dartmusic on 2011-01-26
...

---

### Post by Darwin Award Winner on 2011-01-26
plac is one of them. Just look through the whole file for lines that say "import." Those are all the modules that you need. They might not all be in the Ubuntu repos, so you might have to install them manually. If you need to do this, I recommend setting up virtualenv (which is available in the repos).

---

### Post by StrikerNL on 2012-02-01
> **Darwin Award Winner said:**
> Oh, and you'll need to install some python modules, I suppose.

On ubuntu 10.04.3, this did it for me:

```
# sudo apt-get install python-setuptools
# sudo easy_install -U plac
# sudo easy_install -U quodlibet
# sudo easy_install -U mutagen
```

Might want to add that somewhere.

---

