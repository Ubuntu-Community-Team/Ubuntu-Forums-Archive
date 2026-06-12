---
title: "Batch .epub to .mobi conversion?"
date: 2012-11-17
forum: Mobile Technology Discussions (CLOSED)
---

### Post by suaf on 2012-11-17
Hello,

I am looking for a program/command which would help me convert multiple **.epub** ebooks to **.mobi** format (Kindle-readible). I would prefer to do this via terminal. For single files, I use the Calibre-based **ebook-convert**, but I can't find an option for multiple conversion...

Any info anyone?

Thanks.

---

### Post by drmrgd on 2012-11-17
It seems that Calibre has functionality in the command line:

[http://manual.calibre-ebook.com/cli/ebook-convert.html](http://manual.calibre-ebook.com/cli/ebook-convert.html)

I'm not clear on whether or not that's something you've done before.  If so, great!  If not, try it with one to get a feel for how it works.

Once you know it's working OK, then I think you can probably build a little script to do it batchwise.  The gist will be to write a loop to iterate over all of the .epub files in your collection and feed them to the ebook_covert command with an output name and location.  You might also have a look through all of the commandline options available, as you might find some of them handy

Without having an ebooks, it's a bit hard to test.  But, I would imagine this is a good start of sorts:
```
for book in "<location>/*.epub"; do ebook-covert "$book" "<output_location>/<output_name>" [options]; done
```

Replace all of the stuff that I put in <> with specific information, and take care to be sure you've got the order of things correct by verifying you've called the ebook-covert command with the correct options and whatnot.  You can build up from there, creating variables for the output directories, using some shell replacement techniques for renaming the books, etc.  

The one big thing to remember is to surround your variables with quotation marks so that the shell will be able to handle any books with spaces or special characters in their names.

---

### Post by suaf on 2012-12-27
**@drmrgd:** Thanks a lot! Following your post and this discussion:

[**http://askubuntu.com/questions/60401/batch-processing-tif-images-converting-tif-to-jpeg**]("http://askubuntu.com/questions/60401/batch-processing-tif-images-converting-tif-to-jpeg")

I tried the following and it worked perfectly (no need for quotes, or I didn't put them in the right places, but had no problem with spaces in filenames):

```
$ for book in *.epub; do echo "Converting $book"; ebook-convert "$book" "$(basename "$book" .epub).mobi"; done

```

I guess it can be polished a little bit, for example by adding some option for searching in subfolders; however, I am not really good at that. The option in the quoted thread did not work for me. Anyway, decision found for now.

EDIT: I can't find the "MARK AS SOLVED" option...

---

### Post by Mussorre on 2013-05-27
As i can understand your question their are four ways to edit the mobi file the way you like:
1- if you have the original files that you used to create the mobi you can use them again to create the epub as for example if you have word files you can open them and then save as html filtered then edit with sigil or any html editor the way you like then save as epub which is directely in sigil or use the edited html and build the book using [mobi to ePub]("http://www.vibosoft.com/ebook/convert-mobi-to-epub-mac-win.html.").
 
2- the converted files in calibre (try converting again of mobi to epub after downloading lastest made calibre) which after conversion are epub then save to disk in calibre could be edited in sigil or use calibre to explode epub then edit the html or xhtml in any html editor or just name the extension of file which is epub to zip then unzip then edit internal html then zip again then rename again to epub and use epub viewer to see the results.

---

