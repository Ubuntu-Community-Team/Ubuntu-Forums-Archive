---
title: "giving pdf presentations"
date: 2010-10-14
forum: Multimedia Software
---

### Post by bebops_lost on 2010-10-14
Hey Everyone:

(slight) noob here, I'm having a little trouble with presentations on ubuntu. I created a odp that I was pretty happy with to present to my group last week, but I kept on having these weird problems with all the graphics I inserted. I wanted to use scalable images, but all my eps's ended up having these weird gray lines around the outside of them when they showed up on the projector, and all the .svg images I used had even stranger problems (they looked totally different in the presentation from how they appeared on their own)

So anyway, I got around all of those problems by just exporting the presentation to a pdf. I figured pdf is the failsafe format that just "can't go wrong".

unfortunately I couldn't find a way to actually *present* the pdf. I could create the document, but when I tried to open it in openoffice presentation I got a bunch of weird text. I tried impress and keyjnote, but they both exited as soon as I tried to switch from the first slide (I had a rather large jpg embedded in the 2nd slide, perhaps that had something to do with it.)

anybody know how I can present a pdf document in full-screen mode on the projector? (the error I got in bash is shown below) 
thanks a lot for any help you can offer.


```
me@mydomain:~$ keyjnote presentation.pdf 
...
Using GL_ARB_texture_non_power_of_two.
GC Warning: Repeated allocation of very large block (appr. size 4194304):
	May lead to memory leak and poor performance.
GC Warning: Repeated allocation of very large block (appr. size 1826816):
	May lead to memory leak and poor performance.
GC Warning: Repeated allocation of very large block (appr. size 16764928):
	May lead to memory leak and poor performance.
GC Warning: Repeated allocation of very large block (appr. size 1048576):
	May lead to memory leak and poor performance.
GC Warning: Repeated allocation of very large block (appr. size 6594560):
	May lead to memory leak and poor performance.
Traceback (most recent call last):
  File "/usr/bin/keyjnote", line 4015, in <module>
    run_main()
  File "/usr/bin/keyjnote", line 3576, in run_main
    main()
  File "/usr/bin/keyjnote", line 3567, in main
    UpdateCaption(Pcurrent)
  File "/usr/bin/keyjnote", line 2337, in UpdateCaption
    pygame.display.set_caption(caption, __title__)
TypeError: argument 1 must be string without null bytes, not str
Note: error in file produced by pdftk, hyperlinks disabled.
      PDF parser error message: referenced non-existing PDF object
Unhandled exception in thread started by 
Error in sys.excepthook:

Original exception was:
me@mydomain:~$
```

---

### Post by viralmeme on 2010-10-14
> **bebops_lost said:**
> I created a odp that I was pretty happy with to present to my group last week, but I kept on having these weird problems with all the graphics ..
Can you post a sample of these weird problems?

---

### Post by bebops_lost on 2010-10-15
> Can you post a sample of these weird problems? 

thanks for your reply.

ok, well two things: one, I couldn't figure out how to get rid of the bars at the top and bottom of the screen, and second, when I put one eps figure on top of another (plain white background) I got this gray line showing up around the edge of the one on top (e.g. as shown here) When I tried to use .svg figures, the red triangles in the figure here were black and there were these extra blocks of black space elsewhere on the slide.

Which is fine, really. I gave up on the .odp format, and just used openoffice to export the document to .pdf, and then all of the  gray lines went away. At the moment I just want to know how to present the pdf on the projector.[ATTACH]172401[/ATTACH]

---

### Post by viralmeme on 2010-10-15
> **bebops_lost said:**
> I gave up on the .odp format, and just used openoffice to export the document to .pdf ..

Why not give Lyx a try, people swear by [Lyx]("http://www.lyx.org/")

---

### Post by bebops_lost on 2010-10-15
Hi again.
ok, thanks for the reply, but I think we're having a miscommunication here. The problem is not in creating the pdf -that's already done, and it's perfect. I could use lyx, or latex, or openoffice, or anything else and create pdf slides any number of ways -that's not the problem.

The problem is taking the .pdf (once it's already created and finished and everything) and projecting it onto the big screen, and being able to press the space bar (or mouse click, or whatever) and have the the screen move to the next slide. i.e. to actually ***_present_*** the pdf publicly in a stable way. both keyjnote and impress seem to be having serious problems with this, and I don't understand why.

---

### Post by Simian Man on 2010-10-15
Evince and Okular can both do pdf presentations flawlessly.

BTW if you're technical, you can try using LaTeX with the beamer class to create your presentations.  It outputs pdfs and is extremely high quality.  It has a bit of a learning curve though.

---

### Post by bebops_lost on 2010-10-15
> Evince and Okular can both do pdf presentations flawlessly.


Problem solved: Thanks Simian Man!

And yes, I've used Latex already quite a bit; I'll probably stick to that to make presentations in the future.
thanks again

---

