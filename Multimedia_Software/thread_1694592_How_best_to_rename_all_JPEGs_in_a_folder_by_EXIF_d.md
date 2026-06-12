---
title: "How best to rename all JPEGs in a folder by EXIF date &amp; time stamp"
date: 2011-02-24
forum: Multimedia Software
---

### Post by rocksockdoc on 2011-02-24
In the Windows world where I came from, Irfanview freeware easily renamed a large folder of JPEG photos by EXIF time & date stamps, appending a unique number if the time and date stamps were the same.

Is there an equivalent rename-by-EXIF information batch command in Ubuntu 10.04 Lucid?

For example, change (based solely on EXIF information):

[LIST]
[*]FROM:
[LIST]
[*]DSC_0001.JPG
[/LIST]
 
[*]TO:
[LIST]
[*]20110224_09:34:56am.JPG
[/LIST]
 
[/LIST]

---

### Post by rocksockdoc on 2011-03-02
Nobody?

---

### Post by YesWeCan on 2011-03-02
Well. There is a command line program called **exif** that might be worth looking into.
I gave up on easy methods and ended up writing a Java program to do it.

---

### Post by rocksockdoc on 2011-03-02
> **YesWeCan said:**
> There is a command line program called **exif** that might be worth looking into

Thanks for the idea. It failed, but, I do appreciate the assistance (especially since I had not known about "exif" as a program).

I installed "exif" along with "exiftran" which I already had.

Both seem to do the same thing, which is spit out EXIF information.

[COLOR=DarkRed]** But, neither will rename a file based on the EXIF time and date.**[/COLOR]  :(

So, it looks like I too will need to write a program to convert that information to a program for changing file names of directories of photographs.

Sigh. You'd think we're not the first Ubuntu people to want this capability of naming photographs based on the time and date taken since this is a common feature in Windows freeware.

Here is how I obtained the help for "/usr/bin/exif", for example:
```

$ man exif | col -b > /tmp/exif.man
$ vi !$

  [FONT=Courier New, monospace]exif(1)            command line front-end to libexif           exif(1)[/FONT]
 [FONT=Courier New, monospace]NAME[/FONT]
        [FONT=Courier New, monospace]exif - shows EXIF information in JPEG files[/FONT]
 [FONT=Courier New, monospace]SYNOPSIS[/FONT]
        [FONT=Courier New, monospace]exif [ OPTION ] [ file... ][/FONT]

 [FONT=Courier New, monospace]DESCRIPTION[/FONT]
        [FONT=Courier New, monospace]exif  is  a small command-line utility to show and change EXIF informa&#8208;[/FONT]
        [FONT=Courier New, monospace]tion in JPEG files.[/FONT]
 

        [FONT=Courier New, monospace]Most digital cameras produce EXIF files,  which    are  JPEG  files  with[/FONT]
        [FONT=Courier New, monospace]extra  tags that contain information about the image. The exif command-[/FONT]
        [FONT=Courier New, monospace]line utility allows you to read EXIF information from  and  write  EXIF[/FONT]
        [FONT=Courier New, monospace]information to those files.  exif internally uses the libexif library.[/FONT]
 

        [FONT=Courier New, monospace]Each  input file given on the command line is acted upon in turn, using[/FONT]
        [FONT=Courier New, monospace]all the options given. Execution will be  aborted  immediately  if  one[/FONT]
        [FONT=Courier New, monospace]file is not readable or does not contain EXIF tags.[/FONT]
 

        [FONT=Courier New, monospace]As  EXIF  tags  are read, any unknown ones are discarded and known ones[/FONT]
        [FONT=Courier New, monospace]are automatically converted into the correct  format,  if  they    aren't[/FONT]
        [FONT=Courier New, monospace]already.   Corrupted  MakerNote    tags  are  also removed, but no format[/FONT]
        [FONT=Courier New, monospace]changes are made.[/FONT]
 

 [FONT=Courier New, monospace]OPTIONS[/FONT]
        [FONT=Courier New, monospace]-v, --version[/FONT]
 [FONT=Courier New, monospace]          Display the exif version number.[/FONT]
 

        [FONT=Courier New, monospace]-i, --ids[/FONT]
 [FONT=Courier New, monospace]          Show ID numbers instead of tag names.[/FONT]
 

        [FONT=Courier New, monospace]-t, --tag=TAG[/FONT]
 [FONT=Courier New, monospace]          Select only this TAG.  TAG is the tag title, the short tag name,[/FONT]
 [FONT=Courier New, monospace]          or  the  tag  number (hexadecimal numbers are prefixed with 0x),[/FONT]
 [FONT=Courier New, monospace]          from the IFD specified with --ifd.  The tag title  is  dependent[/FONT]
 [FONT=Courier New, monospace]          on  the current locale, whereas name and number are locale-inde&#8208;[/FONT]
 [FONT=Courier New, monospace]          pendent.[/FONT]
 

        [FONT=Courier New, monospace]--ifd=IFD[/FONT]
 [FONT=Courier New, monospace]          Select a tag or tags from this IFD.  Valid IFDs  are  "0",  "1",[/FONT]
 [FONT=Courier New, monospace]          "EXIF", "GPS", and "Interoperability".  Defaults to "0".[/FONT]
 

        [FONT=Courier New, monospace]-l, --list-tags[/FONT]
 [FONT=Courier New, monospace]          List  all  known    EXIF tags and IFDs.  A JPEG image must be pro&#8208;[/FONT]
 [FONT=Courier New, monospace]          vided, and those tags which appear in the file are shown with an[/FONT]
 [FONT=Courier New, monospace]          asterisk in the corresponding position in the list.[/FONT]
 

        [FONT=Courier New, monospace]-|, --show-mnote[/FONT]
 [FONT=Courier New, monospace]          Show  the  contents  of the MakerNote tag.  The contents of this[/FONT]
 [FONT=Courier New, monospace]          tag are nonstandard (and often undocumented) and    may  therefore[/FONT]
 [FONT=Courier New, monospace]          not be recognized, or if they are recognized they may not neces&#8208;[/FONT]
 [FONT=Courier New, monospace]          sarily be interpreted correctly.[/FONT]
 

        [FONT=Courier New, monospace]--remove[/FONT]
 [FONT=Courier New, monospace]          Remove the tag or (if no tag is specified) the entire IFD.[/FONT]
 

        [FONT=Courier New, monospace]-s, --show-description[/FONT]
 [FONT=Courier New, monospace]          Show description of tag.    The --tag option must also be given.[/FONT]
 

        [FONT=Courier New, monospace]-e, --extract-thumbnail[/FONT]
 [FONT=Courier New, monospace]          Extract the thumbnail, writing the thumbnail image to  the  file[/FONT]
 [FONT=Courier New, monospace]          specified with --output.[/FONT]
 

        [FONT=Courier New, monospace]-r, --remove-thumbnail[/FONT]
 [FONT=Courier New, monospace]          Remove  the  thumbnail  from the image, writing the new image to[/FONT]
 [FONT=Courier New, monospace]          the file specified with --output.[/FONT]
 

        [FONT=Courier New, monospace]-n, --insert-thumbnail=FILE[/FONT]
 [FONT=Courier New, monospace]          Insert FILE as thumbnail.  No attempt is made to ensure that the[/FONT]
 [FONT=Courier New, monospace]          contents of FILE are in a valid thumbnail format.[/FONT]
 

        [FONT=Courier New, monospace]--no-fixup[/FONT]
 [FONT=Courier New, monospace]          Do not attempt to fix EXIF specification violations when reading[/FONT]
 [FONT=Courier New, monospace]          tags.  exif will remove illegal or unknown tags, add some manda&#8208;[/FONT]
 [FONT=Courier New, monospace]          tory tags using default values, and change the data type of tags[/FONT]
 [FONT=Courier New, monospace]          to match that required by the specification.[/FONT]
 

        [FONT=Courier New, monospace]-o, --output=FILE[/FONT]
 [FONT=Courier New, monospace]          Write output image to FILE.  If this option is not given and  an[/FONT]
 [FONT=Courier New, monospace]          image  file  must  be  written, the name used is the same as the[/FONT]
 [FONT=Courier New, monospace]          input file with the suffix ".modified.jpeg".[/FONT]
 

        [FONT=Courier New, monospace]--set-value=VALUE[/FONT]
 [FONT=Courier New, monospace]          Set the data for the tag    specified  with  --tag    and  --ifd  to[/FONT]
 [FONT=Courier New, monospace]          VALUE.   Compound  values  consisting of multiple components are[/FONT]
 [FONT=Courier New, monospace]          separated with spaces.[/FONT]
 

        [FONT=Courier New, monospace]-c, --create-exif[/FONT]
 [FONT=Courier New, monospace]          Create EXIF data if it does not exist[/FONT]
 

        [FONT=Courier New, monospace]-m, --machine-readable[/FONT]
 [FONT=Courier New, monospace]          Produce output in  a  machine-readable  (tab-delimited)  format.[/FONT]
 [FONT=Courier New, monospace]          The  --xml-output  and  --machine-readable  options are mutually[/FONT]
 [FONT=Courier New, monospace]          exclusive.[/FONT]
 

        [FONT=Courier New, monospace]-w, --width=N[/FONT]
 [FONT=Courier New, monospace]          Set the maximum width of the output  to  N  characters  (default[/FONT]
 [FONT=Courier New, monospace]          80). This does not apply to some output formats (e.g. XML).[/FONT]
 

        [FONT=Courier New, monospace]-x, --xml-output[/FONT]
 [FONT=Courier New, monospace]          Produce output in an XML format (when possible).    The --xml-out&#8208;[/FONT]
 [FONT=Courier New, monospace]          put and --machine-readable options are mutually exclusive.[/FONT]
 

        [FONT=Courier New, monospace]-d, --debug[/FONT]
 [FONT=Courier New, monospace]          Show debugging messages. Also, when processing a file that  con&#8208;[/FONT]
 [FONT=Courier New, monospace]          tains corrupted data, this option causes exif to attempt to con&#8208;[/FONT]
 [FONT=Courier New, monospace]          tinue processing. Normally, corrupted data causes an abort.[/FONT]
 

    [FONT=Courier New, monospace]Help options[/FONT]
        [FONT=Courier New, monospace]-?, --help[/FONT]
 [FONT=Courier New, monospace]          Show help message.[/FONT]
 

        [FONT=Courier New, monospace]--usage[/FONT]
 [FONT=Courier New, monospace]          Display brief usage message.[/FONT]
 

 [FONT=Courier New, monospace]EXAMPLES[/FONT]
        [FONT=Courier New, monospace]Display all recognized EXIF tags in an image and the tag contents, with[/FONT]
        [FONT=Courier New, monospace]bad tags fixed:[/FONT]
 

 [FONT=Courier New, monospace]          exif image.jpg[/FONT]
 

        [FONT=Courier New, monospace]Display a table listing all known EXIF tags and whether each one exists[/FONT]
        [FONT=Courier New, monospace]in the given image:[/FONT]
 

 [FONT=Courier New, monospace]          exif --list-tags --no-fixup image.jpg[/FONT]
 

        [FONT=Courier New, monospace]Extract the thumbnail into the file thumbnail.jpg:[/FONT]
 

 [FONT=Courier New, monospace]          exif --extract-thumbnail --output=thumbnail.jpg image.jpg[/FONT]
 

        [FONT=Courier New, monospace]Display a list of the numeric values of    only  the  EXIF  tags  in  the[/FONT]
        [FONT=Courier New, monospace]thumbnail IFD (IFD 1) and the tag values:[/FONT]
 

 [FONT=Courier New, monospace]          exif --ids --ifd=1 --no-fixup image.jpg[/FONT]
 

        [FONT=Courier New, monospace]Display    the  meaning  of tag 0x9209 in the "EXIF" IFD according to the[/FONT]
        [FONT=Courier New, monospace]EXIF specification:[/FONT]
 

 [FONT=Courier New, monospace]          exif --show-description --ifd=EXIF --tag=0x9209[/FONT]
 

        [FONT=Courier New, monospace]Add an Orientation tag with value "bottom - left" to an existing image:[/FONT]
 

 [FONT=Courier New, monospace]          exif   --output=new.jpg    --ifd=0   --tag=0x0112     --set-value=4[/FONT]
 [FONT=Courier New, monospace]          --no-fixup image.jpg[/FONT]
 

        [FONT=Courier New, monospace]Add  a  YCbCr Sub-Sampling tag with value 2,1 (a.k.a YCbCr 4:2:2) to an[/FONT]
        [FONT=Courier New, monospace]existing image and fix the existing tags, if necessary:[/FONT]
 

 [FONT=Courier New, monospace]          exif     --output=new.jpg     --tag=YCbCrSubSampling     --ifd=0[/FONT]
 [FONT=Courier New, monospace]          --set-value='2 1' image.jpg[/FONT]
 

 [FONT=Courier New, monospace]AUTHOR[/FONT]
        [FONT=Courier New, monospace]exif  was  written  by  Lutz  Mueller  <lutz@users.sourceforge.net> and[/FONT]
        [FONT=Courier New, monospace]numerous contributors.  This man page is Copyright ©  2002-2009    Thomas[/FONT]
        [FONT=Courier New, monospace]Pircher and others.[/FONT]
 

 [FONT=Courier New, monospace]SEE ALSO[/FONT]
        [FONT=Courier New, monospace]http://www.sourceforge.net/projects/libexif[/FONT]
 

 

 

 [FONT=Courier New, monospace]exif 0.6.19              2009-11-12                   exif(1)[/FONT]
 

```Here is how I obtained the help for "/usr/bin/exiftran", for example:
```

$ man exif | col -b > /tmp/exiftran.man
$ vi !$

[COLOR=#000000][FONT=Courier][SIZE=3]exiftran(1)                               exiftran(1)[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Courier][SIZE=3]NAME[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]      [FONT=Courier][SIZE=3]exiftran - transform digital camera jpeg images[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Courier][SIZE=3]SYNOPSIS[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]      [FONT=Courier][SIZE=3]exiftran [ options ] file(s)[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Courier][SIZE=3]DESCRIPTION[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]      [FONT=Courier][SIZE=3]exiftran  is  a    command  line  utility to transform digital image jpeg[/SIZE][/FONT][/COLOR]
 [COLOR=#000000]      [FONT=Courier][SIZE=3]images.    It can do lossless rotations like jpegtran, but  unlike  jpeg[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]nail.  It can process multiple images at once.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333][FONT=Courier][SIZE=3]TRANSFORM OPTIONS[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-a     automatic (using exif orientation tag)[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-9     rotate by 90 degrees clockwise[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-1     rotate by 180 degrees clockwise[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-2     rotate by 270 degrees clockwise[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-f     flip vertical[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-F     flip horizontal[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-t     transpose[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-T     transverse[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-nt    Don't rotate exif thumbnail.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-ni    Don't rotate jpeg image. You might  need    this  or  or  the  -nt[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333][FONT=Courier][SIZE=3]          option  to  fixup things in case you rotated the image with some[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333][FONT=Courier][SIZE=3]          utility which ignores the exif thumbnail. Just generating a  new[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333][FONT=Courier][SIZE=3]          thumbnail with -g is another way to fix it.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-no    Don't  update the orientation tag.  By default exiftran sets the[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333][FONT=Courier][SIZE=3]          orientation to "1" (no transformation  needed)  to  avoid  other[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333][FONT=Courier][SIZE=3]          exif-aware  applications try to rotate the already-rotated image[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333][FONT=Courier][SIZE=3]          again.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333][FONT=Courier][SIZE=3]OTHER OPTIONS[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-h     print a short help text[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-d     Dump exif data for the file(s).[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-c <text>[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333][FONT=Courier][SIZE=3]          Set jpeg comment tag to <text>.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-g     (re)generate EXIF thumbnail.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-o <file>[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333][FONT=Courier][SIZE=3]          Specify output file.  Only one input file  is  allowed  in  this[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333][FONT=Courier][SIZE=3]          mode.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]-i     Enable  inplace editing of the images.  Exiftran allows multiple[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333][FONT=Courier][SIZE=3]          input files then.  You must specify either this option or a out[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]CHANTABILITY  or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]Public License for more details.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]You should have received a copy of the GNU General Public License along[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]with this program; if not, write to the Free Software Foundation, Inc.,[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333]      [FONT=Courier][SIZE=3]675 Mass Ave, Cambridge, MA 02139, USA.[/SIZE][/FONT][/COLOR]
 [COLOR=#ff3333][FONT=Courier][SIZE=3]                (c) 2003,04 Gerd Knorr           exiftran(1)[/SIZE][/FONT][/COLOR]
 
```

---

### Post by asmoore82 on 2011-03-02
pyRenamer can do this.

```
sudo apt-get install pyrenamer
```

You have to pick the pictures location in the upper left pane.
Then click the Image tab in the lower pane.

For the replacement pattern, use something like "{imagedate}_{imagetime}".
Using the "Preview" button is highly recommended :D.

> **rocksockdoc said:**
> &#8230;
So, it looks like I too will need to write a program to convert that information
&#8230;
Sigh. You'd think we're not the first Ubuntu people to want this capability&#8230;
Surely you had plans to release this as open source and iron out
the inevitable bugs reported by the community, yes? :razz:

---

### Post by BadgerKid on 2011-03-03
I wasn't aware of pyrenamer, so maybe that solves your needs, OP. I can understand not wanting to "reinvent the wheel" if you don't have to, but another option would be to write your own custom script. 

Another thought: the command 'exiftags' also contains the timestamp information.

---

### Post by jahst on 2011-04-01
know this is a bit old post.. but the answer is exiv2.

[http://linux.die.net/man/1/exiv2](http://linux.die.net/man/1/exiv2)

"
Examples

exiv2 *.jpg
    Prints a summary of the Exif information for all JPEG files in the directory. 
exiv2 -pi image.jpg
    Prints the IPTC metadata of the image. 
exiv2 rename img_1234.jpg
    Renames img_1234.jpg (taken on 13-Nov-05 at 22:58:31) to 20051113_225831.jpg 
exiv2 -r':basename:_%Y%m' rename img_1234.jpg
    Renames img_1234.jpg to img_1234_200511.jpg 

"

I wrote a script a few years ago to batch rename all my files by date and time very quickly... works like a charm for me. A simple bash loop can rename all your photos .. like 1000 .. in a minute or two.

I'd recommend you work on copies first.

---

### Post by d3v1150m471c on 2011-04-01
```

 for i in `ls | grep jpg`; do a=${i/.jpg/.$(date +%T).jpg} && mv "$i" "$a"; done

```why install something when you can handle it with bash :)

```

man sed
man grep
man date
# do above for more info

```

---

### Post by jahst on 2011-04-05
Well, because as far as I can tell your script renames them to the current system date/time.. not the exif date of the photo which is what the poster wanted. If you have a way to do this in bash alone, please share.


Consider this scenario... it happened to me many times.
On vacation some place with 3 different cameras from 3 people...etc.
 
Cameras typically name files using their own conventions.. NCDC, GEDC, etc. 

Therefore, when you put all the photo from the 3 cameras in the same folder, they are organized by Camera name not time taken. Renaming them by exif will nicely merge them all in the correct order.. so for example, you dont see Nikon Camera breakfast, lunch, dinner photos then see them all over again for the GE camera. 


Sorted by exif would look like this.

08:17:30 Nikon Breakfast
08:18:32 GE Breakfast
13:46:22 GE Lunch
13:59:55 Nikon Lunch

It's much cleaner and less repetitive.

Here's the basic code I use.. try yours then mine, especially under the scenarios given above, and see the difference.

```
for i in $(ls *.JPG); do exiv2 -r '%Y%m%d.%H%M%S.:basename:' rename $i; done
```

---

### Post by jensjk on 2011-07-22
gthumb will do the job for you easily

---

### Post by jonycobain on 2012-03-26
The program the user originally was looking for is called "jhead" and can do many useful things like setting files' stampstamps using EXIF metadata or the opposite: changing the metadata based on file's modification date. Of course it can also rename a file using its EXIF info and also another pattern that the user might want to specify.

To install it, just run this:

sudo apt-get install jhead

Hope this helps to future readers of this post.

---

### Post by rocksockdoc on 2012-03-27
I was remiss in not explaining my workaround, which is shown (with other workarounds) here:

[LIST]
[*][Stringing commands together to manage typical digital photo operations]("http://ubuntuforums.org/showthread.php?t=1839153")
[/LIST]
Code excerpt follows ... 

```
# Auto-rotate the originals based on their EXIF orientation tag ...  
jhead -autorot *.JPG 
# Rename the originals to unique names based on their EXIF time/date tag ... 
# Bug: Need a better base name!
for i in *.JPG; do exiv2 -r '%Y%m%d.%H%M%S.:basename:' rename "$i"; done

```The result is a renamed digital photo of the format:
20120317.110323.DSC_1234.JPG 

where the first part is the date, the second is the time, and the third is the original name.


What I haven't figured out yet is how to give the "DSC_1234" part a name based on the topic, e.g., "wedding_pics" or "hawaii_pics" or "ski_trip", etc. such that the name is:
20120317.110323.ski_trip.jpg

---

### Post by Anthony G on 2012-05-15
> **rocksockdoc said:**
> What I haven't figured out yet is how to give the "DSC_1234" part a name based on the topic, e.g., "wedding_pics" or "hawaii_pics" or "ski_trip", etc. such that the name is:
20120317.110323.ski_trip.jpg

As an Ubuntu user, I was researching for the best tool for editing Exif tags and this was the first thread I came across. I wanted to write a script to fix the date of images if the camera had been set to the wrong time.

Since I needed to both read and modify the Exif tags, I read the exiv2 documentation in-depth and thought I should help you out - if you haven't already figured it out yourself (it's one of those ones where you kick yourself because you overthought the problem and it's actually easier than you think).

```

for i in *.JPG; do exiv2 -v -r '%Y%m%d.%H%M%S.wedding_pics' rename "$i"; done
```

---

