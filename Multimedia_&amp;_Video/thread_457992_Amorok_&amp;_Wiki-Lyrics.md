---
title: "Amorok &amp; Wiki-Lyrics"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by ikaroweb on 2007-05-29
I've installed amarok and wili-lyrics plugin on feisty, when i try to get a lyric from a mp3 i give this error:

> Error loading Qt3 GUI backend: Wrong Qt version found (Qt3 expected but Qt4 found)
undefined method `build_google_feeling_lucky_url' for LyricsPlugins::AmarokSing365:Class
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/lyrics_Sing365.rb:34:in `build_song_add_url'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/lyrics.rb:95:in `normalize_lyrics_data'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/lyrics.rb:105:in `normalize_lyrics_data'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/lyrics.rb:180:in `lyrics_direct_search'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/lyrics.rb:333:in `lyrics_full_search'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amaroklyricsmanager.rb:191:in `lyrics_full_search'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amaroklyricsmanager.rb:189:in `each'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amaroklyricsmanager.rb:189:in `lyrics_full_search'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:98:in `on_fetch_lyrics'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:258:in `run_worker'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:243:in `loop'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:243:in `run_worker'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:200:in `main'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:197:in `initialize'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:197:in `new'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:197:in `main'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amaroklyricsmanager.rb:285

Help me please.:(

---

### Post by ikaroweb on 2007-05-29
Nobody? :(

---

### Post by ikaroweb on 2007-05-30
I've installed libqt0-ruby1.8 and now i've this error:

> undefined method `build_google_feeling_lucky_url' for LyricsPlugins::AmarokSing365:Class
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/lyrics_Sing365.rb:34:in `build_song_add_url'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/lyrics.rb:95:in `normalize_lyrics_data'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/lyrics.rb:105:in `normalize_lyrics_data'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/lyrics.rb:180:in `lyrics_direct_search'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/lyrics.rb:333:in `lyrics_full_search'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amaroklyricsmanager.rb:191:in `lyrics_full_search'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amaroklyricsmanager.rb:189:in `each'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amaroklyricsmanager.rb:189:in `lyrics_full_search'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:98:in `on_fetch_lyrics'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:258:in `run_worker'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:243:in `loop'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:243:in `run_worker'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:200:in `main'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:197:in `initialize'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:197:in `new'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amarokscript.rb:197:in `main'
/home/ikaroweb/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amaroklyricsmanager.rb:285

---

### Post by ptinolv on 2007-07-02
Hi,

I don't know if you manage to make it works. Try to execute this command ( it worked for me ) :
```
rm .kde/share/apps/amarok/scripts-data/wikilyrics.xml 
```

I hope it will work.

Bye

---

### Post by alexisj on 2007-07-04
Hi
Try to disable Sing365 as lyrics-site and restart amarok.
Do that without playing music.

It worked for me

see also:
[http://www.kde-apps.org/content/show.php?content=35151&forumpage=5](http://www.kde-apps.org/content/show.php?content=35151&forumpage=5)

:)

Check also depedencies (ruby, qt-ruby...)

---

