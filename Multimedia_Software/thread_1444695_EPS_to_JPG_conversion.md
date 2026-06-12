---
title: "EPS to JPG conversion"
date: 2010-04-01
forum: Multimedia Software
---

### Post by d0.higgs on 2010-04-01
Hi,

I have generated some .eps figure which I needed to show one by one. I converted them using convert file.eps file.jpg but the generated files were kind of blurred (not much, but they are not of the same quality as the .eps files)
Is there anything to do to get a good conversion?
Also, which is better, is/are there any image viewer package that would help show the .eps files as .jpg files?
I have tried, gthumb, gqview, f-spot, image magic (display).

Thanks in advance

---

### Post by jobix on 2010-04-01
You could try ghostview - gv - to view the .eps files.

Out of curiosity, what did you use to generate the .eps files?

---

### Post by d0.higgs on 2010-04-01
I use a package called ROOT (you can google it) and it generates it's output histograms in many formats. But my script uses this format because we include it in our publications with LaTeX.

Many other packages help you generate this format.

Back to my problem. I changed the format to .png

Thanks

---

### Post by Chronon on 2010-04-01
I think Inkscape can rasterize (i.e. export a bitmap).

---

### Post by jobix on 2010-04-02
When I used to write publications in LaTeX, I'd simply include the .eps files in my main .tex file without any conversion and it came out just fine. Here's some old stuff I was able to find:
> 
\begin{figure}[htb]
\begin{center}
{\resizebox{3.0in}{3.0in}{\includegraphics{myfig.eps}}}
\end{center}
\caption{put in some caption here}
\label{mylabel}
\end{figure}

---

### Post by d0.higgs on 2010-04-02
> **jobix said:**
> When I used to write publications in LaTeX, I'd simply include the .eps files in my main .tex file without any conversion and it came out just fine. Here's some old stuff I was able to find:

Jobix,

Thanks so much for the tip. I do use .eps for LaTeX, but I want the jpg files (currently .png) for my presentations. openoffice does not consider .eps as known format.

---

### Post by Chronon on 2010-04-02
I thought this was the issue.  See if Inkscape will work for you. It's a bit slow and tedious if you have lots of images but it will allow exporting to bitmap.  A dedicated (CLI) rasterizer would be nice, but I haven't found a suitable one so far.

---

### Post by Rendsvig on 2010-11-16
I used this hassle-free:

[http://www.terminally-incoherent.com/blog/2007/04/23/convert-ps-and-eps-images-to-jpeg/](http://www.terminally-incoherent.com/blog/2007/04/23/convert-ps-and-eps-images-to-jpeg/)

I used F-spot to crop the images afterwards.

---

### Post by gcordoba on 2011-04-19
Hi,
just install imagemagic, then:

$> convert foo.eps foo.jpg

---

