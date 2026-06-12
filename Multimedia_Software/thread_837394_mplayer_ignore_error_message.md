---
title: "mplayer ignore error message"
date: 2008-06-22
forum: Multimedia Software
---

### Post by k3kiaze on 2008-06-22
Hi,

When i play certain avi files with Mplayer, I get this error during playback "overflow in spectral RLE ignoring".. Since it's an 'ignore' message is there an option prevent 'ignore' errors in Mplayer? If not how do I disable all error messages from Mplayer? thanks.

---

### Post by Subban on 2009-01-18
I am going to go ahead and bump this as I can't find a solution using search and its a problem I also have, lots of video files throw an error in mplayer that I really do not need to see, they work normally.

---

### Post by andrew.46 on 2009-01-18
Hi,

You can probably try either of these commandline options and see if they meet your needs:

> 
       -quiet
              Make  console  output  less verbose; in particular, prevents the
              status line (i.e. A:   0.7 V:   0.6 A-V:  0.068 ...) from  being
              displayed.  Particularly useful on slow terminals or broken ones
              which do not properly handle carriage return (i.e. \r).



and:

> 
       -really-quiet (also see -quiet)
              Display even less output and status messages than  with  -quiet.
              Also suppresses the GUI error message boxes.


Is this what you were after?

Andrew

---

### Post by Subban on 2009-01-19
> **andrew.46 said:**
> Hi,

You can probably try either of these commandline options and see if they meet your needs:

Many thanks for the reply.

--really-quiet looks just the job as it is the GUI error windows that are a problem for me, I had checked the --help for mplayer but had only seen the normal --quiet which didn't affect GUI errors.

Now the second problem, how do I add this flag for gmplayer to use when I double click an avi for eg.

I tried right click an avi, choose properties and add a custom command as follows:

gmplayer --really-quiet

After the change double clicking an avi does nothing at all, a quick google didn't come up with a fix, but admittedly I was rushing between jobs.

---

### Post by andrew.46 on 2009-01-19
Hi Subhan,

> **Subban said:**
> Now the second problem, how do I add this flag for gmplayer to use when I double click an avi for eg.

I don't personally use the gmplayer but I note that there is a section in SMPlayer for adding such options. Can I suggest SMPlayer rather than gmplayer? You can of course have both on your system with no problem.

```
$ sudo apt-get install smplayer
```

Options --> Preferences --> Advanced --> Options for MPlayer


All the best,

Andrew

---

### Post by nike984 on 2009-01-19
> **Subban said:**
> Many thanks for the reply.

--really-quiet looks just the job as it is the GUI error windows that are a problem for me, I had checked the --help for mplayer but had only seen the normal --quiet which didn't affect GUI errors.

Now the second problem, how do I add this flag for gmplayer to use when I double click an avi for eg.

I tried right click an avi, choose properties and add a custom command as follows:

gmplayer --really-quiet

After the change double clicking an avi does nothing at all, a quick google didn't come up with a fix, but admittedly I was rushing between jobs.

you can edit the config file in ~/.mplayer

gedit ~/.mplayer/config

then under [default], add (really-quiet="1"),
so that the config file look like this

```
[default]
# Write your default config options here!
really-quiet="1"


```

save the config file and mplayer will ignore any error message

---

### Post by Subban on 2009-01-19
Thank you Andrew and Nike.

I am trying Smplayer as I hadn't used it to date, I have always prefered a video player having a separate playback window which has no toolbars etc but I am always open to suggestions of something better to at the very least try.

The solution Nike has indicated was perfect and gotten rid of the error windows that some video files had caused to pop up. So that is the correct solution for the Mplayer problem for myself and I would expect the OP who can hopefully pop back and mark this as Solved.

Many thanks again :]

---

### Post by pw_f100_220 on 2009-03-29
I have been trying to get -really-quiet in my config file for a few days, and really-quiet="1" stops gmplayer completely.  BASH says "Option really needs a parameter at line 140" which is the line in the config with really-quiet="1"

what am I doing wrong?

---

### Post by andrew.46 on 2009-03-29
Hi pw_f100_22-

> **pw_f100_220 said:**
> I have been trying to get -really-quiet in my config file for a few days, and really-quiet="1" stops gmplayer completely.  BASH says "Option really needs a parameter at line 140" which is the line in the config with really-quiet="1"

what am I doing wrong?

I will admit that I don't use gmplayer but the following works well in my ~/.mplayer/config:

```
really-quiet=1
```

The quotation marks around the 1 suggested in a previous post are not really necessary I suspect but this should make no difference. Does MPlayer fail from the commandline as well?

Can I suggest 2 things?

[LIST=1]
[*]Try opening a file from the commandline with really-quiet=1 in place
[*]If this fails post the contents of your ~/.mplayer/config here
[/LIST]

A final suggestion is to use a different gui for MPlayer, my own preference is for SMPlayer.

Andrew

---

### Post by pw_f100_220 on 2009-03-30
Thanks andrew.46 for a quick reply!  However;

the quotation made no difference as you expected

opening from command line with "-really-quiet" worked wonderfully, but no 
error message is ever displayed from the terminal in the first place...which is how I usually play my media files.  I always liked seeing the output from the terminal.  I like a "loud" terminal output...it makes me feel smarter:)

my mplayer.conf file is unchanged without the -really-quiet nonsense, so there shouldn't be any clues in there.

as for your final suggestion of using SMplayer, I prefer not to have a graphical version in the first place since the keybindings are most intuitive...SO, if you know way to click a file and have it open in the terminal mplayer...I believe all of my Mplayer questions will be forever answered.  I often use a graphical file manager to browse my collection and then open it with the terminal (my love for BASH is unending)...but I sometimes just want to click the file and send it to terminal.

...not that i've ruled out using a new graphical interface...

---

