---
title: "The new Okular (V. 21.12.3) won't open annotations made in an older version of Okular"
date: 2023-04-05
forum: Multimedia Software
---

### Post by mountredoubt on 2023-04-05
Hi everyone, I hope someone can help me out with this.

After my old Kubuntu 18.04 laptop died, I've set up a new one with Kubuntu 22.04 LTS. I have lots of pdf-files annotated in Okular on my old system, but when I open them on my new system with Okular Version 21.12.3, some annotations won't open. More specifically, sticky-notes do open, but notes associated with in-line annotations like highlighted text or strike-through don't.

Does anyone know a fix or a work-around? Or some other software I could install that will open those notes? 

Also, can you recommend some other software for annotating PDF? I love Okular, but I've had this problem with other people who work with other platforms/software not being able to read my annotations.

Thanks!

---

### Post by TheFu on 2023-04-05
I hadn't looked at Okular in about a decade, perhaps longer. It was a great tool.  At first, I didn't like how the annotations were stored in separate files, but then came to depend on that architecture.

I see they changed it so that external annotation files aren't supported anymore.  I feel for the devs, since they were probably getting negative comments for having annotations separate and then when that was merged into the PDFs, now the people who preferred the separate files complain.  One guy disliked it enough to write [https://github.com/ahnorton/annotation-manager](https://github.com/ahnorton/annotation-manager) .  This might help, though I doubt that Okular from 18.04 had the annotations separate. Still, it might be able to pull them from existing PDFs, shovel the annotations to separate files and correct any required changes along the way.  

For annotations, you'll need to find a tool that uses the standard annotation that Adobe does.  I've read good things about Master PDF. Think it is $50-$80.  People seem to like it.  Even if Adobe supported Linux, even just a little, I'd rather give money to anyone else. ;)

---

### Post by mountredoubt on 2023-04-05
Thanks. I wonder if it's the problem with separate annotations though. I have loads of notes on in-line annotations in my old files, **but it looks like Okular no longer supports them at all.  I've tried adding a note to highlighted text in the new Okular version and it didn't work. - **I take that back. It does work at least for some in-line annotations, and those are visible if I open the file in masterpdf.

I've looked at  [https://github.com/ahnorton/annotation-manager](https://github.com/ahnorton/annotation-manager), thanks, but it doesn't look like it will help me access my old annotations.

The only thing that has worked for me so far, is to open the annotated file in acrobat under *******, save it, then open it with masterpdf. Then I could see the notes on my in-lline annotations. What a mess.

---

### Post by mountredoubt on 2023-04-05
Hey, I think I've found the problem, and the solution, haha. It is really stupid. 

The new Okular **can** create new and open existing notes on in-line annotations, but! If under Tools the option "Text selection" is toggled on, then it is virtually impossible to click on the annotation without hitting the text. If you hit the text, Okular thinks that you want to select the text and not the annotation. You really have to be very careful to hit the very edge of the highlighting to open the annotation. But if you activate any other option under Tools - Browse, Zoom, Area Selection - doesn't matter, then it becomes much easier to click on in-line annotations.

However, the problem still remains that other pdf readers, like mastgerpdf, won't see old Okular annotations, though they will see the new ones.

---

### Post by td-safemail-tmp on 2023-11-19
Thank you for posting the solution. :KS
> **mountredoubt said:**
> haha. It is really stupid.  .    

not so stupid, and the interface is very confusing.       

    Help says that if you want to move (and resize) an annotation, you need to hit **Ctrl** and drag the annotation.
However _this does work ONLY if icon "text/image/table select" is NOT selected._

---

