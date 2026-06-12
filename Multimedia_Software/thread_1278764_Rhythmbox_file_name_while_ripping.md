---
title: "Rhythmbox file name while ripping"
date: 2009-09-29
forum: Multimedia Software
---

### Post by tmetzcc325 on 2009-09-29
Hey all,

I use Rhythmbox to rip my CDs into ogg files.  I have two questions related to this:

1) I want to have Rhythmbox name the folders for the albums as Artist - Album Year - Album Title (%aa - %ay - %at).  This is not one of the options in the drop-down list in the Preferences > Music tab.  I tried changing to this pattern by changing the /apps/rhythmbox/library_layout_path key in gconf-editor, but as soon as I do, when I pull up the Preferences > Music tab, the drop-down list is set to blank, and the /apps/rhythmbox/library_layout_path key is updated to blank as well.  How can I rip using this naming format?

2) The pattern I use to name the songs themselves is %ta - %tN - %tt (Artist - Song # - Title).  This is one of the options in the drop-down list, and that is how it is saved in the /apps/rhythmbox/library_layout_filename key.  For some reason, though, it is replacing all the spaces with underscores.  Where is this setting?  On old versions of Ubuntu (which I've been using since Breezy), this never happened.

Any ideas?

Thanks,
Tom

---

### Post by donato roque on 2009-10-01
Hi tmetzcc325, 
    
    I also use Rhythmbox v 0.12.0 and it's a great application.  But then my collection is now 40 GB in its separate partition-about 7,000 tracks.  So tagging them needs a stand alone application.
    
    I use Easytag and I really recommend it.  Reading your post, I think it's right up your alley.  It's in the repos.
    
    Yes, this is not THE answer to your questions but it could solve your problem without you realizing it.

---

### Post by tmetzcc325 on 2009-10-01
Thanks, donato, I also use EasyTag.  This just seems like the sort of thing that should be configurable - not limited to a few options.

And the issue with the underscores - I have no idea what is causing that.  Never used to be that way.  Still not hard to fix with EasyTag though.

---

### Post by tmetzcc325 on 2009-10-09
Found the reason for the underscores, at least -- there is a key in configuration editor called library_strip_chars.  This key, when activated, converts spaces to underscores.  I unchecked it, and now the filenames have spaces instead, just like I wanted.  There is no option for this in the Rhythmbox front-end, so I am not sure how it was clicked - must have been an errant movement with the mouse-hand.  Hope this helps anyone in this same predicament.

Would still love a way to change the options for the filename and directory structure when ripping files, but I suppose that will have to be discovered in the future.

Thanks for everyone's suggestions.

Tom

---

### Post by arthur.afarias on 2010-04-04
Hi! I have the same problem as you tmetzcc325. The Gconf is not letting me put a different pattern of defaults.

Oi! eu tenho o mesmo problema que você tmetzcc325. O Gconf nao está me deixando colocar um padrao diferente dos predefinidos.

---

