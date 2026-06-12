---
title: "banshee crashing when adding music to playlist"
date: 2009-11-08
forum: Multimedia Software
---

### Post by pythonscript on 2009-11-08
When I try to add music to a playlist by either right clicking the song and selecting Add to Playlist or by dragging and dropping the song onto the playlist, banshee immediately crashes. I started it from the terminal, and here's the output:

```
[Info  21:38:55.641] Running Banshee 1.4.3: [Ubuntu jaunty (development branch) (linux-gnu, i486) @ 2009-03-22 18:04:14 UTC]
[Info  21:38:57.151] All services are started 1.347126s
[Info  21:38:58.059] nereid Client Started

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: table CorePlaylistEntries has 5 columns but 4 values were supplied
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00000] 

```Any ideas here? This is the output after I start it and *immediately *attempt to add a song to a playlist. Is there something I'm missing here? Thanks!

---

### Post by zenkaon on 2009-11-08
I've never really liked banshee or rhythembox, you should try exaile.

I know it's not a solution to your problem, more of an alternative.

---

### Post by directhex on 2009-11-09
Looks like something I had where I ran 1.5.1 then downgraded to 1.4.3. Sound familiar?

---

### Post by pythonscript on 2009-11-09
> **directhex said:**
> Looks like something I had where I ran 1.5.1 then downgraded to 1.4.3. Sound familiar?

Completely forgot about that part. Yes, I ran 1.5.1 from the banshee PPA, but it crashed too... so I downgraded to the current one in the repos. How did you fix this after downgrading?

As for exaile, I've tried it, as well as amarok, and banshee has been my favourite one by a long shot. Thanks for the suggestion!

---

### Post by directhex on 2009-11-09
> **pythonscript said:**
> Completely forgot about that part. Yes, I ran 1.5.1 from the banshee PPA, but it crashed too... so I downgraded to the current one in the repos. How did you fix this after downgrading?

As for exaile, I've tried it, as well as amarok, and banshee has been my favourite one by a long shot. Thanks for the suggestion!

Well, I upgraded again. You can try to tweak it manually via the "sqlite" command, but it's probably not worth it. Karmic ships with 1.5.1 FWIW

---

### Post by pythonscript on 2009-11-09
I upgraded again using the PPA from banshee's site, but now when I go to play a track, this error pops up:

```
Problem with Player Engine

Object reference not set to an instance of the object
```

How do I fix this? I would love to use the new version of banshee (and I tried upgrading to Karmic, and on my system right now, it's simply too riddled with bugs, and I'm not at all happy with the "improved" boot performance) but I can't even play a track now... I can add music to the playlist, though! One problem solved, another one comes! 

This problem only happens about every other time I start it, though, since it's working now... Any ideas how I can fix this?

---

### Post by pythonscript on 2009-11-11
This problem seems to have gone away... I haven't updated my laptop since I installed banshee, but it now appears to be working flawlessly. Maybe a reboot? I didn't think ubuntu was in need of such reboots after installing software, but maybe it's just a random correlation. Anyways, thanks for the help! I'm tentatively marking this thread as solved, since the problem is *technically* solved, even though I have no idea why. I love the new banshee, I must say!

---

