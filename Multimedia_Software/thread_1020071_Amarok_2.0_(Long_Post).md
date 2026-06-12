---
title: "Amarok 2.0 (Long Post)"
date: 2008-12-23
forum: Multimedia Software
---

### Post by jimbo99 on 2008-12-23
Amarok 2.0 (Build Date: Dec 15, 2008) on KDE 4.1.3

Had some time to install Amarok 2.0 and peruse it's features.  I was quite familiar with Amarok 1.x so I didn't feel my task would be too difficult.  Things should have gone well, and I was expecting some of the negative reviews to be wrong.  Launching it began a long series of oddities and incorrect assumptions by the program's author.  I was really amazed at how much was still wrong, and how noticeable most of those were.  I remember writing software years ago and found myself amazed at how many errors people found that I hadn't tested for, even though I was working very hard at testing my work.  This project reminds me of that.  I'll just get started and hope that what I write in this review isn't too disjointed, and that people understand what I'm getting at.

Even though I have used Amarok 1.x for years, upon viewing Amarok 2.0 at first start I was totally lost and there were immediate errors that I find difficult to see why the Amarok team didn't identify them right away.  For instance, upon launching it the first time I had an error message about plugins.  I was told via a message to try again.  Amarok 2.0 didn't open so I launched it a second time.

With a second attempt it loaded.  Even though it was up on my screen I was at a loss to figure out what to do next.  My first thought was to drag and drop folders into it to play back music, and in doing so nothing happened.  I tried repeatedly to no avail.  Paying attention to the prompts, messages, and cursor indicators, I was given nothing to indicate something was wrong;  I wasn't even given the mouse pointer &#8220;circle with the line through it&#8221; (as you see most often in other programs--and within Amarok 2.0 at various times).

Being at a loss I then resorted to my regular attempts at the venerable right click.  Voila, I got something that said &#8220;Add applet&#8221;.  I did so.  Not knowing what to add I just added what I could.  I added a few applets.  It made things look messy and disorganized but at least it was progress.  Continuing further I tried other things.

Note:  I had to revise the Last.fm comments.  I managed to get it to work.  But I did discover that the Last.fm applet allows you to put in any password and it blithely accepts it with no message as to whether you put in the wrong password.

In order to continue trying to make progress I then moved on to other ways to add songs to the playlist.  I had chosen to not build a collection because in past versions this feature was only semi-useful to me.  I had various issues with database corruption and slow performance.  In order to avoid this I looked for other options and saw the &#8220;Files' button on the far left of the main window. 

I clicked on &#8220;Files&#8221; and added some music stored in my Linux home folder.  Let's just say I was exstatic when it began to play them.  I was happy because I remember all the difficulties in Amarok 1.x to get it to play something even when the songs were listed in the playlist.  In early releases of Amarok 1.x the program would crash or not play back or required more files to be installed from other sources (even though this last part is still required).  I was happy that I didn't have to address that problem and that this was some progress.  I then added a few more songs and tried to edit a few ID3 tags.

About this time I decided that it would be nice to try to clean up things and organize them.  I chose to add and remove some applets in order to make this look like something more than a messy garble of embedded windows of the wrong size and postion.  The two main ones were the Lyrics and the Wikipedia applets.

I found in attempting to get things organized that the Wikipedia applet can't be resized manually and won't automatically resize to fill the big gray gaps in the main window.  I thought to myself, well, maybe these gray gaps are for other applets, so I attempted to add more.  

(Note:  As I was using Amarok it crashed and when I re-launched it things seemed more organized.  I make some comments about that later in this review.)

In Amarok 1.x one of the most annoying elements is when the playlist moves to the next song (even if it is the same artist) and the Wikipedia information is updated &#8220;again&#8221;, thus making you loose your reading position.  Needless to say, it is very annoying.  I decided to test to see if this was the case in Amarok 2.0.  Happily it doesn't force you to reload the Wikipedia information after each song.

Since you can't resize the Wikipedia applet it makes it more difficult to use because you have to scroll far too much.  While scrolling around I found that if you click too fast on the scrollbars it will begin to scroll on it's own (and not just from queued clicks).  It will cause the Wikipedia applet to become unusable, and the only way out of it is to completely close the program and start over.

As it turns out, the Lyrics applet won't and can't be resized either.  I found other issues with the Lyrics applet that some may consider bugs and others just polish issues.  I found that upon its failure to locate lyrics, rather than giving us a clear entry with some professionally done graphic indicating the lyrics aren't available, we get a rather primitive &#8220;programmer&#8221; oriented text output about &#8220;not found&#8221; and some link showing the URL that was used in the attempt to retrieve the lyrics.

When manually selecting the lyrics text using the mouse (left click and drag) and when you move the pointer to the top of the window the selected text begins to flash and you have to keep reselecting in order to get what you really want.  You can't use it to scroll to the top to retrieve all the lyrics text from the bottom up.  What's odd is that if you start at the top and select by dragging down it works fine.

I would like the change the font size of the lyrics (not asking to change the font, just the size).  It doesn't appear possible.  On a large screen that font seems small.

I decided I'd look at streaming and chose to add a rock radio station.  It took a while for it to respond and that's O.K. considering all the radio stations it listed, but the problem is that there were too many and most of them had extremely cryptic names or there were so many duplicates that it was pointless to try.  This is not solely Amarok 2.0's fault but considering that this is &#8220;a given&#8221; (so many and so disorganized) I would have expected Amarok to try to tidy it up a bit.  At this point I randomly chose a radio station.  I clicked on a radio station and boom!! Amarok crashed.

Still interested I moved on...  I'll try to categorize some of what I found.

Settings
I looked at the settings to determine if there were as many options (or options with similar functionality to Amarok 1.x).  There are far fewer options, though the ones there did seem similar to those in Amarok 1.x.  For some this may be a good thing, but for a seasoned Amarok 1.x user absent settings are not positive things.

The OSD allows you to specify the color of the text but not the color of the background.  It is also set to use true transparency except it isn't that transparent and you can't specify how much transparency you want.  The yellow stars on the semi transparent background of the OSD is difficult to read.  In fact, the yellow is hard to read on the default color scheme of Amarok 2.0.

Playlists
If there was a playlist feature that stands out and above the idea of just dragging and dropping your music files into a playlist and then clicking play I can't find it.  Maybe there's some real intent on organizing albums by artist and making playlists from that.  In reality though there's little I'll use it for other than just dragging and dropping music to play.

Sometimes I will want to drag and drop a song to be positioned before a song already in the playlist.  Other times I will just add and queue the songs.  With Amarok 2.0 it seems quit difficult to add one or more songs to the end of the playlist even if you have scrolled to the bottom first and using mouse (drag and drop) move and hover while looking for where the song should go just doesn't cut it.

It wasn't readily apparent how to mass tag files.  An album that didn't receive the proper ID3 tags when the CD was ripped results in an unclean playlist.  In Amarok 1.x you could add all the albums from a single artist and use the mass tagging to make the name consistent.  Even when ripping a CD and using CDDB to look them up in order to tag them properly the CDDB entries can be inconsistent and there's a need to clean this stuff up.  Maybe the mass tagging is there and someone can point it out to me.  

I did select all the titles by an artist in my play list and right clicked and chose to edit the tags.  What happened is that at one point it put me on one page of the dialog box and another time I tried it I was put on a completely different page.  Even if this is a result of the dialog box having &#8220;a memory&#8221; it would seem logical to select the most logical page (or even the same start page) every time.

I was looking for a way to clear the playlist and start over.  Below the playlist are some buttons.  I clicked on the one that indicated that it was for clearing the playlist.  Doing so resulted in me being presented with a message box in the lower left corner of the Amarok 2.0 Window that told me that the option to clear the playlist wasn't possible as there was no signal handler.  The message box had a close button but it cleared itself before I had a chance to read it all as I noticed it a few seconds after I had clicked the clear playlist button.  The playlist did clear.  The message wasn't presented as a result of me clicking it twice as the button becomes grayed out when the playlist is empty.

Any editing of a tag of a file in the playlist causes the Local Collection list to collapse and you loose your position.

There's no way to sort by artist nor by album, or anything else in the playlist.

Missing Features
There are many noticeable features missing such as the ability to queue songs.  The equilizer.  Visualizations.  Tagging (see above under Playlists.)

Adding Files
I clicked on the &#8220;Files&#8221; option (on the far left) and decided to add songs to the playlist from some folders.  (Note:  I did this because when I attempted to drag and drop folders onto the playlist (as stated earlier) nothing happened.) I traversed to the location where I normally keep my music files.  After locating an artist and album I wanted to play, I would single click it to select. It would automatically add them to the playlist even if I didn't want that to happen.  What I wanted to do was multiselect so that I could select the first track and then control+click to select the others (or shift+click).  To a new user that would be very annoying as you have to keep going to the playlist to remove the songs you don't want.  Please don't say click only on the ones you want, because that's vacuous as it doesn't meet the way normal human beings do things on computers.  The good news is that this won't be a major issue (though it should be fixed) when they get drag and drop working properly.

Collection
In Amarok 1.x I used to use the Collection manager, but over time the database became corrupt and difficult to work with.  This one is no less difficult, though I don't know about the stability of the database feature.

Though I said earlier that the Collection option had given me trouble in the past with Amarok 1.x I still intended to ease of use test it here.  I like the idea of having a &#8220;Collection&#8221;, but when it hinders my attempts at finding and playing music I tend to end using those features.

In attempting to use it, when I would double click on an &#8220;album&#8221; entry it would seem to add it to the playlist even though all I was trying to do was expand the album to display the titles of the tracks. Apparently the only way to expand the branch is to click on the plus sign (which seemed tiny, and unresponsive).  I'm still not satisfied with how collections were handled in Amarok 1.x, nor am I convinced that they are handled well in 2.x.

Performance wasn't very good but once it was up I was able to use it, though there were oddities and bugs in it.  For instance...

The &#8220;Group By&#8221; feature of the collection manager seems to work sufficiently.  What's odd is when you switch from artist/album to album only it takes a long time to sort even when there aren't that many songs in the collection.  And, it then triggers a massive retrieval of album art.

When using the Collection list and right clicking on an album then choosing edit it (and then editing it) saving the changes causes the whole Local collection list to collapse, thus causing me to loose my place and forcing me to search again.

When perusing my collection I found an album that had a long title (listing all the artists names that must have participated in the making of the album).  I scrolled to the far right in the collection list, then clicked on the name which immediately jumped me to the far left.  I then &#8220;right&#8221; clicked on the name and *boom*, Amarok crashed presenting me with a fatal error and a signal 11 (SIGSEGV) error.  The audio that was playing played for a bit longer and then became staticy and ceased playing.

Scripts
I decided to look at the available scripts.  There were only a few so I chose to download more.  The list was retrieved without issue.  I found a script I wanted.  I chose to install it.  That also happened without issue but I was told I had to restart Amarok to make it happen.  

The Music Explorer was the script I downloaded.  When it launched it told me that there were some issues with something or the other, then it proceeded to do it's job.  A window popped up at the bottom left of my screen that gave me the option to turn it on.  I chose to do that but I got a message dialog box indicating that it was already turned on.

As I went though the options, such as &#8220;configure&#8221; the dialog boxes were placed at the various corners of the screen.  The only bad part is that on a 24&#8221; monitor these dialog boxes are way out there so I have to turn my head just to read them.  Most dialog boxes are put in the center of the screen, not in the far corners.

Maybe I'm not sure what the Music Explorer is about.  What caught my eye in all this is that once I moved my attention to the plalist I found songs by other artists had been added to my playlist.  I think that needs to be fleshed out with some information as to what the purpose is and what the user should expect.  I'd hate to have a ton of songs show up and blow away the ordering of the songs in my playlist.

Oddities
I'm going to just list with some minor explanation some of the odd things about the program.  Consider them bullet items.

After the crash and when I returned to it Amarok seemed to be organized.  If that isn't totally funny. 

When I double click on the far left component of the main Amarok window the windows resize incorrectly.

The play/next/previous/pause/stop, etc buttons are too big and there's no apparent way to shrink them.

The song progress bar is too big and you can't shrink it except by resizing the main Amarok window.. 

You can't change that you want the &#8220;volume %&#8221; displayed all the time and the only way to see it is to move your mouse pointer over the top of it.

The mute button next to the volume display is not a toggle.  Normally you would set a volume.  If someone comes in to your room to talk you might want to click the mute temporarily.  Then when you click mute a second time your volume would end up where you were before you muted.  In Amarok 2.0 the way the author mutes it is by setting the volume to 0.  This wouldn't be bad if he recorded the current volume setting and set it back when you click mute again to unmute.

Apparently Amarok doesn't support the iphone 2g (at least).  Adding the devices applet and plugging in the iPhone results in nothing happening.  And the Media Devices applet results in gray block in the Amarok main window.  The reason why is that it seems to switch you from your current &#8220;applet&#8221; page to the this applet's page (even if there is room on the first page to load that applet by slightly resizing the other applets).

I was looking at the last played applet and ranking the songs when I realized that there were more than 4 songs I had recently listened to.  I looked to see if there was a scrollbar control.  It seems that it is missing so tried to scroll with the mouse scroll wheel.  This appeared to do something.  It caused the Last Played and the Lyrics applets to reposition themselves farther up in the main window (for no good benefit).  I was able to scroll back down, but having the scroll wheel do this seems out of place and unnecessary.

The album art retrieval seems to be off the mark a lot.  It was rare that I found album art that matched the song I was playing.  It made some solid guesses though and once in a while it found the right one.

When you click to hide the controls on the far left of the Amarok window it causes the applets section of the window to shift to the left, leaving the playlist where it was and a huge blank gap in the middle of the main window.  I guess you could have more applet pages and they'd become visible.  Nonetheless, it is strange behavior that obfuscates what little beauty Amarok 2.0 has.

When you click to bring back the portion hidden by clicking on the far left controls the applets that were drawn to the left side are not repositioned instead they drop below the other controls (such as the Collection list) on the main window.  The only solution is to close Amarok down and restart it.

When I clear the playlist it doesn't clear the Lyrics applet's window.  Now, some may consider it to be a blessing but it might be considered inconsistent behavior.  At least provide an option to allow it to be cleared at the same time.

I also found that many things just didn't appear to do much of anything.  I found some applet that allowed me to indicate how much I liked a song, yet it appeared to have no function beyond that, even though the icons indicated that there was more to it than just that.

Opinions
The Window colors are too bright and there's no way to set your own (this is another of those missing features that used to be in Amarok 1.x).   The thing is it doesn't comply with the color scheme of the environment in which it is used.  Programs are no longer KDE or Gnome (or any other for that matter).  Programs in Linux are programs to be used in Linux regardless of the desktop manager and therefore need to comply with the settings of that environment. VLC does this.  It takes advantage when the KDE 4.x libs are installed and yet it still complies with the theme when run under gnome.  I would guess at some point the intent is to allow skinning.  For those that want to keep their programs working consistently in their customized Linux these programs should comply.

The developers seem to have taken the unilateral position that they should change the name of the hotkey features that rely on the &#8220;win&#8221; (or &#8220;super&#8221;) key.  In Amarok 1.x the key was called the &#8220;super&#8221; key and in programs such as Compiz they are still referred to as the super key.  In Amarok 2.x they chose the term &#8220;meta&#8221; which doesn't really make any sense as there's no meta &#8220;anything&#8221; attached.  If you could call the super key the meta key (because it changed the behavior of the key you pressed in conjunction with it) then you could also call the Alt and Control (and even the shift) meta keys.

On the plus side, at least the first menu item on the menu bar is no longer named &#8220;engage&#8221;.

The author of Amarok 2.x seems to be averse to tabs.  He's attempted to write the program without using a tabbed interface and instead has chosen a weaker UI design model. A major example of this is the applet's pages.  You move between them not by clicking on a tab but by clicking on the left or right arrow at the bottom of where the applets are displayed.  This really is only slightly more difficult than just using a tabbed method.  The author though hasn't completely given up on tabs as the &#8220;About Amarok&#8221; still uses them. The use of tabbled dialogs is very sparse.  The controls on the far left hand side of the window isn't a tabbed interface.  It is a series of buttons that have been resized and set to display vertically instead of horizontally.

There's a feature that allows you to download album art.  As many of us know album art is drawn down from Amazon and according to their rules and in order to comply the album art is removed after a certain amount of time.  Someone on the Amarok forums suggested that they be retrieved from Last.fm instead.  Even if the author of Amarok doesn't want to, and still thinks Amazon should be used, this is a program after all, and that should be an option.

The author seems to have made decisions arbitrarily for the users and decided to program this in a way that met his needs.  If he were to introduce this to the &#8220;Windows XP/Vista&#8221; world he'd be lambasted out.  Sure there'd be some that thought it was cool, but with all this unpolished work the negatives will outweigh the positives.

I hate to say it, but this reminds me of a programmer that takes a hammer and screwdriver to a users workstation when they complain of problems with something he programmed.

The Admin on the Amarok forums was hostile to numerous people that were asking questions in an attempt to get answers to why such and such feature failed or caused a crash.  There was almost always the attitude (though he may not have expressed it outright) that the users were idiots and I feel his comments demonstrated that clearly.

One example was where someone indicated he had a lot of music and he wanted it in the playlist.  The response from the site Admin was to question why he would want to add that many songs.  The response in and of itself didn't seem too strange, but clearly he didn't understand the user and has no intention to try.  The way he phrased it was an attempt to demean the guy.  Most everyone will want many songs in their playlist if not just for the sake of having a long playlist that will play for a long time.  Not everyone is a couch potatoe watching TV.  Some play music constantly in the background and that's why we would want long playlists.

The program is very slow on a dual core AMD 6000+ with 3.25 gigs of RAM.  It also seems to slow down as I used it more and more.  Memory use seems good.  It's hard to tell.  The program seems to become sluggish but when you look at how much RAM it is using and how much of the CPUs it is utilizing these values are quite low.  Maybe it has to do with the applets or other programs that Amarok calls.

It uses the same old icon.

I appologize that this is so long, it's just that there's so much &#8220;odd&#8221;.  This certainly isn't Amarok of old.  This, in my opinion should not be considered anything more than a beta (maybe even an alpha) release.

---

### Post by martunes13 on 2008-12-23
Two of my favorite KDE applications were Amarok and ktorrent.  They were fast and functional.  Now, I feel sad regarding Amarok 2.0.  It's just missing a lot of the things I loved about Amarok 1.x.  The same is true with ktorrent.  It's slow and they lumped all the files downloading and uploading in one screen.  It's also difficult to load torrents.  Maybe it's just my personal preference but I'm a bit disappointed with these two programs.  Hopefully they'll be able to improve upon these because of the release early, release often mindset.  So I hope they'll improve over time.  For now I'm using either transmission or deluge instead of ktorrent.  As for an Amarok replacement, I don't know yet.  Any suggestions?

---

### Post by jimbo99 on 2008-12-24
Amarok 1.x is still very viable.

---

### Post by jimbo99 on 2008-12-24
I had spent some time working on reviewing Last.fm as I use it with many of the ways I play music.  You create an account on Last.fm and then you can tell programs such as Amarok to log into your Last.fm account and update it with the songs you play.  That way your music can somewhat follow you around.  There's a last.fm applet that's free for the iPhone and various other ways of getting your music profile updated.  You can even link to your friend's music and listen to their music and get a sense of their tastes or even discover artists you like.

When I first tried to get Last.fm to work I had issues with it not updating my profile and I couldn't get it to play streams such as my personal playlist radio.

Yesterday I found that I could get it to work if I just entered a valid password.  It seems Amarok will allow you to set up Last.fm and accept any password without error.  (I corrected my password and Amarok's Last.fm began working.)

This morning I began working with it a bit more and noticed that it was still updating my profile.  I thought that after the playlist that I had running in Amarok 2.0 that I'd like to just play my last.fm radio.

Within Amarok 2.0 you can just add the stream as an entry in your playlist.  So, I dragged and dropped my personal radio into the playlist.  I noticed that there were other entries that were added so I right clicked on them and chose to remove them.  I then noticed that Amarok had stopped updating my last.fm profile.

I guess it is still buggy in other ways.

---

### Post by Open-SuSe-A-Me on 2008-12-24
I agree, i don't understand why the Amarok developers would change the best audio player of all time (IMO) so much.  

Then again, i feel the same way about KDE4.  KDE3 was perfect and they completely changed it.  Am i the only person who feels the Oxygen style is the ugliest thing ever?

But KDE's mistakes have made me realize how much better GNOME is.

---

### Post by jimbo99 on 2008-12-25
With KDE 4.x there's no real desktop, so the majority of the space is wasted.  The idea of widgets controlling the desktop is just wrong.  A desktop is a desktop just like the clock or calendar pad on your desktop doesn't rule your desk.  You use your desktop for everything.  That little desktop widget is a farce at best.  The KDE guys need to rethink or their product will fall off the map.

---

