---
title: "Mythmovies - help needed - Canada"
date: 2008-07-27
forum: Mythbuntu
---

### Post by kyfehr on 2008-07-27
I am trying to setup mythmovies. I live in Canada and have read that the default does not work in Canada.

However, everytime that I try to follow the directions to setup this grabber [http://www.gossamer-threads.com/lists/mythtv/users/337417](http://www.gossamer-threads.com/lists/mythtv/users/337417) (the gmythmovies.pl script)

I can not get it to work. Does anyone know of a grabber that works in Canada.

Thanks.

---

### Post by nerver on 2008-10-17
I am having the same problem unfortunately. Using the grabber from the link above I can get movie times and everything when I run the following command in a terminal:

perl /directory/gmythmovies_0.2.pl $pcod xxxxxx

but if I put this command in mythmovies (or if i just add the location without "perl" at the start) i get nothing when i run it.

I think it may have something to do with the fact that mythmovies makes you add the radius amount in? But I don't really know, that is just a guess.

Has anyone gotten myth movie listings to work in Canada?

---

### Post by Fonikar on 2008-11-15
I'm having the same problem with gmythmovies. I'm sure it's a rookie error, but if I call /usr/bin/gmythmovies_0.2.pl %z in mythmovies I get an error that it failed to run gmythmovies_0.2.pl

If is use terminal and the command perl /usr/bin/gmythmovies_0.2.pl $pcod xxxxx

(where xxxxxx is my postcode)

it works just fine

Does anyone have any ideas why it won't run from Mythmovies???

---

### Post by aviynw on 2008-11-17
I'm having the same problem with the default ignyte script with a u.s. zip code.  I get xml output when typed into the terminal but when I type in the same thing for the movie time settings and then go to "movie times" nothing shows up.

So, it seems to be a problem with mythtv not with the scripts.  I'm not familiar with how things get done here, might a bug report be in order?

---

### Post by jeefm on 2009-03-16
I have same problem.  Does anybody have a solution?
thx

---

### Post by ahood on 2009-05-30
I just upgraded from Mythbuntu 7.10 to 8.04 LTS and the mythmovies plugin initially did not work. The problem was an error message about the ignyte script.

I figured out that I needed a different grabber script and the gmythmovies script ([http://www.marcusandzoe.com/mythtv/gmythmovies_0.3d.renametodotpl](http://www.marcusandzoe.com/mythtv/gmythmovies_0.3d.renametodotpl)) did work for me. 

*Note: I live in the US.*

Below are the steps I used to get it to work.

**Step 1.** Downloaded the script to my user home directory (/home/username)

**Step 2.** Renamed the script.

> mv gmythmovies_0.3d.renametodopl gmythmovies.pl

**Step 3**. Edited the script

> nano gmythmovies.pl

Inserted a '#' at beginning of line 56 to comment it out.

> #   my $pcod = $ARGV[0];	# Postcode passed in as parameter

Deleted the '#' at the beginning of line 57 to uncomment it out and replaced '47715' with my zipcode.

> my $url = 'http://www.google.com/movies?near=68243'; # US postcode

Inserted a '#' at beginning of line 62 to comment it out.

> my $url = 'http://www.google.com.au/movies?near=' . $pcod;

Lastly, saved gmythmovies.pl by pressing ctrl+x on the keyboard.

**Step 4.** Made gmythmovies.pl executable

> sudo chmod 755 gmythmovies.pl

**Step 5.** Update mythmovie config in mythbuntu frontend

Navigate to Home --> Utilities/Setup --> Setup --> Info Center --> Mythmovies

In the Grabber text box, entered the path to gmythmovies.pl

> /home/username/gmythmovies.pl

*Note: Only the path to gmythmovies.pl should appear. Delete all other text.*

---

### Post by nerver on 2009-05-31
Hey ahood,

Thanks for your input on this. I dl'ed the script you linked to and I was able to make it work for Canada off the the steps you gave, the only difference was that in addition to commenting out line 56, I had to comment out line 62 and then remove the # from the beginning of line 57 and add my city to the url So in my script line 57 reads:

 my $url = 'http://www.google.com/movies?sc=1&near=vancouver';

so for Canadian mythtv folks if you do it this way and exchange the vancouver part of the url for your own city it will work in mythtv.

Thanks ahood :)

---

### Post by ahood on 2009-05-31
> **nerver said:**
> Hey ahood,

Thanks for your input on this. ...

Thanks ahood :)

Very much welcome. I was hoping the instructions would be of use to someone. Glad to see that it has.

Thank you for the added explanation. I neglected to fully explain that it is necessary to modify the line specific to one's area. Your addition completes that part. 

Thanks also goes to philledwards who wrote the script originally (I think) and updated by Marcus ([http://www.gossamer-threads.com/lists/mythtv/users/338675](http://www.gossamer-threads.com/lists/mythtv/users/338675)). Because I have been looking forward to using the mythmovies plugin, I am very appreciative that this script is available.

Regards,

Al

---

### Post by luketb on 2009-06-20
Thank you for the work put in to making and modifying this script.

I am however also having trouble making it work from within the MythTV information center.

I have changed the path to the script in the setup section, I can run it from the command line without issue, I cannot see any errors in the mythfrontend log or syslog.

Any directioon or tips would be appreciated.

I am running 9.04.

---

### Post by ahood on 2009-06-22
> **luketb said:**
> Thank you for the work put in to making and modifying this script.

I am however also having trouble making it work from within the MythTV information center.

I have changed the path to the script in the setup section, I can run it from the command line without issue, I cannot see any errors in the mythfrontend log or syslog.

Any directioon or tips would be appreciated.

I am running 9.04.

Hello,

I don't know if I can help, but will try. Need a bit more information.

1. Did you download the script from here [http://www.marcusandzoe.com/mythtv/gmythmovies_0.3d.renametodotpl](http://www.marcusandzoe.com/mythtv/gmythmovies_0.3d.renametodotpl) ?

2. Did you rename and edit the script?

3. Which line(s) of the script was edited and what was/were the change/s?

4. What is the output when you execute the script from a command prompt?

---

### Post by SeaHuck on 2009-07-25
I  change Line 46 to initialise genr it worked after that.

my $genr;

to

my $genr=0

---

### Post by bcgrown on 2009-12-29
This is all the output I get with Debug=1:

```
dave@dave-laptop:~/Downloads$ ./gmythmovies.pl v6e4r2
<?xml version="1.0" encoding="utf-8"?>
<MovieTimes>

DEBUG url = http://www.google.ca/movies?near=v6e4r2
</MovieTimes>
```

Anybody have a clue what's going on?  I know roughly nothing about Perl.

---

### Post by jlibster on 2010-06-16
Hi fellow Canadian Residents. You won't believe it but after some looking I discovered I had to adjust the script to account for changes by Google. New separators for data sometimes the delimiters between a new movie info block are  irregular (5% don't always add the "-" at the beginning). I've hacked out the script (its ugly with changes) but it works for Canada now and other if comment/uncomment the proper lines. If anyone wants to clean it up and make it more professional be my guest. When I have some time, I'll give it a proper "once over" but at least its functional (at least in my minimal tests, meaning it works for me in my area) You can download it here:

[http://www.evolveit.ca/script_contributions/gmythmovies_0.4b.pl.zip](http://www.evolveit.ca/script_contributions/gmythmovies_0.4b.pl.zip)

Enjoy Canadians (and others communities unable to use version 0.3b due to Google changes)

Additional data (and headache): There appears to be an additional problem with the MythMovies plug-in. I've validated the XML generated with my changes and they work, even made sure it was well formatted XML, but MythMovies insists that the script "terminates abnormally" (even with all parameters hard-coded). Even the original US-only script to examine their XML. The script from ignyte seems no longer work. I tested the script with a US zip code and get a message about going to ignyte.com to see what services are there. So it appears they ALL fail now. I will try to crawl through the source code of MythMovies as time permits to see why its rejecting the valid XML given by the script (or what it requires, I'm guessing updates were done). If anyone has additional insight (so I can avoid a code crawl) I'd be grateful for your suggestions. Thanks all hopefully we shall prevail.

---

### Post by bcgrown on 2010-06-16
I've found this script to work perfectly:

(Edit:  Not my script.  See the author's link for more info.)

```

#!/usr/bin/perl

# Regular updates to this script can be found here:
# http://github.com/Jonty/Googlemovies

use warnings;
use strict;
 
use LWP::Simple;
use HTML::Entities;
use HTML::TreeBuilder;
use XML::Writer;
 
# Google url. You shoudn't need to change this unless fetching totally fails.
# Just change the domain to your local google, i.e. google.com to google.de
my $googleurl = "http://www.google.com/movies?near=";
 
# Set to 1 to fetch only first page of results
my $fetch_pages = 10;
 
# Otherwise we can get complaints when unicode is output
binmode STDOUT, ':utf8';
 
# Fetch the postcode/location to use from the args
# You can also use city name, "New York", "London"
my $location = join '+', @ARGV; # join args with '+' to be able to pass i.e. "New+York" in the url
 
if (!$location) {
    print "No postcode/location passed in arguments!\n";
    exit;
}
 
my $out = '';
my $xml = new XML::Writer(
    OUTPUT => $out,
    DATA_MODE => 1,
    DATA_INDENT => 2
);
 
$xml->xmlDecl();
$xml->startTag('MovieTimes');
 
my $start = 0;
parse_html(fetch_html($googleurl.$location));
 
$xml->endTag(); # MovieTimes
$xml->end();
 
# Tada!
print $out;
 
sub fetch_html {
    my $response = get(shift() . '&start='.$start);
 
    if (!defined $response) {
        print "Failed to fetch movie times, did you pass a valid postcode?\n";
        exit;
    }
 
    return $response;
}
 
sub parse_html {
    my $tree = HTML::TreeBuilder->new();
    $tree->parse(shift);
    $tree->eof;
 
    my @rows = $tree->look_down('_tag', 'div', class => 'theater');
    foreach my $row (@rows) {
        $xml->startTag('Theater');
        $xml = parse_cinema($xml, $row);
 
        my @movierows = $row->look_down('_tag', 'div', class => 'movie');
        $xml->startTag('Movies');
        $xml = parse_movies($xml, @movierows);
        $xml->endTag(); # Movies
 
        $xml->endTag(); # Theater
    }
 
    if (--$fetch_pages > 0) {
        my $url = parse_navbar($tree);
        if ($url) {
            parse_html(fetch_html($url)) if $url;
        }
    }
}
 
sub parse_navbar {
    my $tree = shift;
    my $next_start = $start+10;
    my $return_url;
    my $rooturl = $googleurl;
    $rooturl =~s/^(http:...*?)(\/.*)$/$1/i;
 
    # look for a link with 'start=$nextstart'
    if (my $navbar = $tree->look_down('_tag', 'div', id => 'navbar')) {
        my @links = $navbar->look_down('_tag', 'a');
        foreach my $a (@links) {
            if ($a->attr('href') =~/^\/movies\?.*start=$next_start$/) {
                if ($a->attr('href') !~/^http:/) {
                    $return_url = $rooturl.$a->attr('href');
                } else {
                    $return_url = $a->attr('href');
                }
                $start = $next_start;
                last;
            }
        }
    }
    return $return_url;
}
 
sub parse_cinema {
    my ($xml, $cinema) = @_;
 
    my $name = ($cinema->look_down('_tag', 'h2', class => 'name'))[0]->as_text;
    $name =~ s/[\xC2\xA0]+//g; # Myth can't handle UTF8 nbsp
    $xml->dataElement('Name', $name);
 
    my $address = ($cinema->look_down('_tag', 'div', class => 'info'))[0]->as_text;
    $address =~ s/[\xC2\xA0]+//g; # Myth can't handle UTF8 nbsp
    $xml->dataElement('Address', $address);
 
    return $xml;
}
 
sub parse_movies {
    my $xml = shift;
 
    foreach my $movierow (@_) {
        $xml->startTag('Movie');
 
        my $name = ($movierow->look_down('_tag', 'div', class => 'name'))[0]->as_text;
        $xml->dataElement('Name', $name);
 
        my $info = ($movierow->look_down('_tag', 'span', class => 'info'))[0]->as_text;
        if ($info) {
            if ($info =~ /Rated\s+(\w+)/i) {
                $xml->dataElement('Rating', $1);
            }
 
            if ($info =~ /(\d+hr\s+\d+min)/i) {
                $xml->dataElement('RunningTime', $1);
            }
        }
 
        my $showtimes = ($movierow->look_down('_tag', 'div', class => 'times'))[0]->as_text;
        if ($showtimes) {
            $showtimes =~ s/[\xC2\xA0]+//g; # Myth can't handle UTF8 nbsp
            $showtimes =~ s/\s+/, /g;
            $xml->dataElement('ShowTimes', $showtimes);
        }
 
        $xml->endTag(); #Movie
    }
 
    return $xml;
}

```

---

### Post by jlibster on 2010-06-17
Yes this script does work perfectly! (Yea!!)  BUT...(you knew there was one), most noobie users who run the script will get an error and go "What the...!" they just setup & run this gem. To those of you who are trying the Google Script above, before you run it install the following package (only had to install one package to get this script working on Ubunth 9.10):

libxml-writer-perl

Without this package a dependency is broken in the perl script. The code is nice, beautiful and all the rest. And it encodes the output so MythTV doesn't break when running the script. What one should do (maybe I will) is combine the original script (with adjustments for Google changes), and use additional methods to properly encode the output for MythTV to properly read so that it can run with no additional package installation. Baring that, an install "Readme" should go with this script. (Yes I know the code tells the story but most general users don't want to read code) 

The one thing MS did right was, they figured out that if something isn't easy to use out of the box, most people won't bother use/buy it. Since we want to get more MS converts to this side of the fence, we should pay attention to ease of use/install for non-techies.

---

### Post by bcgrown on 2010-06-17
If you are going to put a lot of effort into this,  maybe you should consider maintaining MythMovies itself.  As it stands,  MythMovies is slated to be removed from MythTV 0.24.

[[COLOR="Blue"]See here for details.[/COLOR]]("http://svn.mythtv.org/trac/changeset/24939")

---

