---
title: "Lilypond"
date: 2007-07-29
forum: Multimedia Production
---

### Post by Guitar John on 2007-07-29
> xxx@xxx-desktop:~$ lilypond
GNU LilyPond 2.10.5
Usage: lilypond [OPTION]... FILE...

Typeset music and/or produce MIDI from FILE.

LilyPond produces beautiful music notation.
For more information, see [http://lilypond.org](http://lilypond.org)

Options:
  -b, --backend=BACK               use backend BACK (gnome, ps,eps,
                                     scm, svg, tex, texstr)
                                     default: PS
  -d, --define-default=SYM=VAL     set a Scheme program option. Uses #t if VAL is not specified
                                     Try -dhelp for help.
  -e, --evaluate=EXPR              evaluate scheme code
  -f, --formats=FORMATs            dump FORMAT,...  Also as separate options:
      --dvi                        generate DVI (tex backend only)
      --relocate                   relocate using directory of lilypond program
      --pdf                        generate PDF (default)
      --png                        generate PNG
      --ps                         generate PostScript
      --tex                        generate TeX (tex backend only)
  -h, --help                       print this help
  -H, --header=FIELD               dump a header field to file BASENAME.FIELD
  -I, --include=DIR                add DIR to search path
  -i, --init=FILE                  use FILE as init file
  -j, --jail=USER,GROUP,JAIL,DIR   chroot to JAIL, become USER:GROUP
                                     and cd into DIR
      --no-print                   do not generate printed output
  -o, --output=FILE                write output to FILE (suffix will be added)
  -p, --preview                    generate a preview of the first system
  -s, --safe-mode                  disallow unsafe Scheme and PostScript operations
  -v, --version                    print version number
  -V, --verbose                    be verbose
  -w, --warranty                   show warranty and copyright

Report bugs via [http://post.gmane.org/post.php?group=gmane.comp.gnu.lilypond.bugs](http://post.gmane.org/post.php?group=gmane.comp.gnu.lilypond.bugs)

xxx@xxx-desktop:~$ 



I installed Lilypond using Synaptic.  There is no icon anywhere to launch the program.  When I type *Lilypond* into the terminal, this is the output.  But I can't do anything with that.  Am I missing something obvious? 

-John

---

### Post by kevinlyfellow on 2007-07-30
Lilypond is a lot like teX or lateX.  You need to write the file, and then lilypond will convert it to pdf and ps.  So for instance if you write a file with this is in:
```
{
        \time 2/4
        \clef bass
        c4 c g g a a g2
}
```

and name it new.lily, you can 
```
lilypond new.lily
```
and get a pdf with
[IMG]http://lilypond.org/web/images/example-1[/IMG]

edit:  Here is the crash course on using it [http://lilypond.org/web/switch/howto](http://lilypond.org/web/switch/howto)

---

### Post by kevinlyfellow on 2007-07-30
I've discovered a front-end for it called denemo.  Just
```
 sudo apt-get install denemo
```

---

### Post by Guitar John on 2007-07-30
As it turns out, I already had *Denemo*.  And there is a Lilypond extention under *Save As*.  Ok, I'm making some progress.  

Alright, let me play around with this for a while and see if I can:
-create some notation
-not break anything

Thanks.

---

