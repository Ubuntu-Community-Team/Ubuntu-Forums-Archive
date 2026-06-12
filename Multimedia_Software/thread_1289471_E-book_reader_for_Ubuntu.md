---
title: "E-book reader for Ubuntu"
date: 2009-10-12
forum: Multimedia Software
---

### Post by noob555 on 2009-10-12
Does anyone know a good Ubuntu program for reading e-books and simple text pdf files?

I'm looking for something that could emulate the Amazon Kindle or Iphone reader applications.  Black text on plain background and EASY on the eyes for long reading assignments.

Any help would be appreciated.

Thanks!

---

### Post by azmo35 on 2009-10-12
Hi,maybe this site help you [here]("http://www.brighthub.com/computing/linux/articles/48344.aspx")

---

### Post by noob555 on 2009-10-12
Thanks, but that's not really what I'm looking for.  The Iphone app and the Kindle employ a screen with minimal glare and white light emanating from the screen.  It looks like this ([http://www.mediabistro.com/mobilecontenttoday/original/Eucalyptus_iphone.png]("http://www.mediabistro.com/mobilecontenttoday/original/Eucalyptus_iphone.png")) and this ([http://www.blogcdn.com/www.tuaw.com/media/2009/03/kindle2header.png](http://www.blogcdn.com/www.tuaw.com/media/2009/03/kindle2header.png)[http://www.blogcdn.com/www.tuaw.com/media/2009/03/kindle2header.png]("http://www.blogcdn.com/www.tuaw.com/media/2009/03/kindle2header.png"))This makes the experience much easier on the eyes.  

Is there anything like that on Linux at all?

---

### Post by Onesimus on 2009-10-12
So are you looking for hardware or software ?  Both examples you have given are hardware devices.

---

### Post by kidux on 2009-10-12
Try Calibre. Works great for my Sony PRS-505.

---

### Post by kumoshk on 2009-12-16
If you really want software (for Ubuntu, to read .txt files on Ubuntu), it sounds like what you want is an e-book reader that will let you customize font and background colors.

If you're like me, then a glaring white screen isn't nice on the eyes for many hours of reading. It makes sense, after all, since a white screen produces the most light. Real books don't glow&#8212;so a black background is actually a closer match to the real thing, even if it looks different, I think. I prefer a black screen with dull or pastel-colored text, in full-screen. Sometimes I read with a gray font (e.g. #777777 or #AAAAAA, depending on the screen brightness). Sometimes I use a darker red one (if the font is very thick). Sometimes I use pastel colors (since they are soft and easy to look at). Pretty much, I like any color that doesn't create a glare against the black, and is still easy to see. Anyway, a black screen doesn't produce as much light or radiation as a white screen&#8212;so physically-speaking, it should be better for you, if your eyes can handle it.

Anyway, I also recommend using a larger font than you're probably used to. It might sound weird, but it can make for more enjoyable reading (even if you can see small print just fine). This is partly because it makes the lines shorter in width, if you have word wrap on.

I haven't seen a lot of e-book readers that are designed to work well with plain text. Here are the readers I've tried that seemed at least semi-worthwhile:
&#8226; Fbreader (on Karmic&#8212;not before): this is kind of cool, although it doesn't do line breaks on plain text (but it does magically seem to give you a hypertext-capable table of contents that actually works); it'll save your position and you can customize colors
&#8226; TxtReader: It's kind of inconvenient to set up, but it works and let's you customize things. Line breaks also work.

If you're interested, I'm actually making my own desktop/laptop e-book reader with customization and plain text in mind. It's functional now, and I use it every day, just about, but, it has a ways to go before I release it. Anyway, some key features of it, so far, are these:
&#8226; Handles UTF-8 (Unicode), and you can set a secondary encoding, if you want.
&#8226; You can fully customize text and background colors, fonts, font sizes, etc. (and it remembers them)
&#8226; There's a full screen mode
&#8226; You can use keyboard shortcuts to increase and decrease font size as you read, and it doesn't change the top line of the screen.
&#8226; It remembers the last file loaded and takes you to your place (unless you configure it otherwise)
&#8226; It's set up to work with multiple user accounts on your computer
&#8226; There's a bookmarks menu (kind of like in Firefox, only with files instead of URLs); it'll save your position with the bookmark. If you re-bookmark the same file it'll just update your position.
&#8226; There are keyboard shortcuts for most things.
&#8226; Moving the screen up and down actually goes by line&#8212;so, if you read from the top, it'll look neat instead of having it skip several lines in a choppy fashion where it sometimes has a partial line showing
&#8226; You can associate .txt files with it and have it open them. (Stange as it sounds, most e-book readers won't work with this.)
&#8226; You can open .txt files with it from the command-line. (Strange as it sounds, most &#8230;)
&#8226; It has a standard Gtk menu, and not one of those funky toolbars that most e-book readers have.
&#8226; You can remove and bring back the menubar with a keyboard shortcut.

I still need to spruce up the bookmarks, as right now you can't remove them, unless you do it from the bookmarks.txt file. It only does plain text so far, though I have plans for certain other things. I only have linux to compile it on (64-bit and 32-bit), currently, although it probably would compile fine on Windows or Mac, if you had the compiler set up for it.

For PDF files, I think your best bet is to find a PDF viewer that lets you customize colors. There are some that let you do it, but it might take a while to find the setting for such, if you're not used to such. If you have 32-bit Ubuntu, I think Adobe Reader will actually let you do that. Some of the free ones will, too, but I forgot which. The rest might change if you change your system colors, but I don't guarantee that.

---

### Post by rewyllys on 2010-07-02
> **kumoshk said:**
> . . . . If you're interested, I'm actually making my own desktop/laptop e-book reader with customization and plain text in mind. It's functional now, and I use it every day, just about, but, it has a ways to go before I release it. . . .

What's the current status of your e-book reader?  Are you still working on it? getting close to releasing it?

It sounds quite interesting.

---

### Post by kumoshk on 2010-07-02
> **rewyllys said:**
> What's the current status of your e-book reader? Are you still working on it? getting close to releasing it?

It sounds quite interesting.

Ah, thanks for your interest. :) I'm still working on it, although only casually (so it may or may not be a while). I don't need to do too much more before I release it, although there are a few issues. Recently, I added a status bar that tells you what line (out of how many) you're on, as well as what percentage of the book you've read. I've also added a stopwatch to it (so you can time your reading; it shows up on the status bar). I want to make it so it can tell you your words per minute (that shouldn't be too hard). You can remove bookmarks now. I also made it so you can change the indents flexibly (with or without shortcut keys) as well as the alignment&#8212;this helps a lot when full paragraphs are a single line and you have the program maximized. I've fixed the tabs so they're not huge anymore.

Here are the things I would like to finish before I release it officially:
&#8226; Add search functionality
&#8226; Add document statistics functionality (word count, etc.)
&#8226; Complete the help section
&#8226; Make it so you can have more than one bookmark per book (right now, if you bookmark an already bookmarked book, it just updates it). I want to make it so you have a current bookmark, and can update that one still&#8212;but, I want another option to add a new bookmark, under a cascading menu for that book, and the ability to name it.
&#8226; Add a jump to line option
&#8226; Add a countdown timer (as opposed to a stopwatch) with an alarm.
&#8226; Fix the scrollbar issue. In order to implement a certain feature, I had to make some difficulties with the scrollbar. I think I have an idea of how to fix that, though.
&#8226; Keep track of reading history in a log file. People might like to know when they read what.
&#8226; Add potential for per book preferences (e.g. so one file can have different indents than another).
&#8226; Add the ability to open txt files directly from an online location. I.e. open URL. It might be nice to have a Gutenberg browser, too, but I don't know if I'll do that soon.
&#8226; Autoscrolling, by line, as well as smooth (with the ability to change the speed with keyboard shortcuts, while it is autoscrolling)
&#8226; Zipped text file support (various compressed formats)
&#8226; Add icon art
&#8226; Decide on a name for the program.
&#8226; Add an optional method to reformat Gutenberg texts so that each paragraph is a single line. This way one can take advantage of the justified alignment and the indents/margins more readily. I'll need to make an algorithm so that it'll know not to do this to such as poetry quoted within a novel, though (i.e. only combine lines that are longer than a certain length, unless it's the last line in a paragraph).
&#8226; Add an optional method to Replace ASCII characters with their formatted equivalents (i.e. -- for &#8212;, 1-10 for 1&#8211;10, "" for &#8220;&#8221;, '' for &#8216;&#8217;, ... and . . . for &#8230;, remove double spaces and other excess whitespace, and such)
&#8226; Decide on a license (it'll probably be GPL, but I'm not sure, yet)

Here are some things I want to add, but might not until a later release:
&#8226; Italics, bold and underlined text
&#8226; Optional profanity filters (still working on a good algorithm so that it looks like it's not being filtered)
&#8226; Encrypted file support (i.e. so you can open password-protected files; I'd love to do this through GNU Privacy Guard, but I might have to settle for Gnutls or something).
&#8226; A windows and Mac version. I tried compiling in Windows, and though it compiles, some things don't work properly (such as the mouse wheel, and the bookmarks, and it didn't work at all through Wine); so, I'll have to fix those issues when I get some time and a Windows computer to mess around with. I'm not sure how well this works on a Mac without modifications. If it proves difficult with Vala, I might translate it to Python for those versions (although that would make it slower, likely, and make updates take longer).
&#8226; An optional tabbed interface for reading multiple books at once. Right now it always does multiple instances for opening multiple files.

Anyway, as it stands right now, this e-book reader is great for reading a book from beginning to end (or several books). It's not that great for jumping around and studying various parts of the same book in one sitting&#8212;but I plan to fix that.

I think my biggest obstacle is that I've been being lazy about figuring out how to make temporary GTK input boxes pop up (e.g. to name a bookmark, enter a line number to jump to, enter a search query, etc.) I've heard of how to do this from scratch, but it looks like it might take some time to make for the first time. So, if anyone reading this has already done such, and wants to help things go a little faster, feel free to contribute some code in that regard. I really need to get the search up and running&#8212;so I might just have to whip myself into shape and do it within the next while. Lately, I've been adding features based on how much it bothers me not having them. It's been bothering me not having the search for some time now&#8212;so I better hop on that. [EDIT: I've found a great example of how to do such as this. So, it shouldn't be too long.]

---

### Post by KegHead on 2010-07-02
Hi!

Calibre works great, also have a sony prs-300.

KegHead

---

### Post by xtracool_protik on 2010-07-03
Calibre works nice for me, though u may know its not a pdf viewer but an organizer. I use document viewer for pdfs, which saves previous reading state and have an option to invert colors so I see white on black which is more appealing to me than black on white.
 I'm looking forward to pdf reader kumoshk mentioned as well

---

### Post by kumoshk on 2010-07-03
> **xtracool_protik said:**
> I'm looking forward to pdf reader kumoshk mentioned as well

I didn't mention a specific PDF viewer. My e-book reader is just for plain text files. However, adding italics and such may come a lot sooner than I had thought. So, it should be able to handle at least some rich text tags.

---

