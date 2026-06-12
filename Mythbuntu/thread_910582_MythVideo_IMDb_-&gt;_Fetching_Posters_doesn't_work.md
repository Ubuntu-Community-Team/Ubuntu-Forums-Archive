---
title: "MythVideo IMDb -&gt; Fetching Posters doesn't work"
date: 2008-09-04
forum: Mythbuntu
---

### Post by Stevi on 2008-09-04
Hi,

as described in the thread title poster-fetching in mythvideo doesn't work on my machine. I'm using Mythbuntu 8.04.1 with weekly builds. I played around with the IMDb script but it still doesn't fetch any posters. At the moment I get the following message: ```
A poster exists for this item but could not be retrieved within the timeout period
```
Google doesn't help in [this case](http://www.google.de/search?num=20&hl=de&client=firefox-a&rls=org.mozilla%3Ade%3Aunofficial&hs=FTM&q=%22a+poster+exists+for+this+item+but+could+not+be+retrieved+within+the+timeout+period%22&btnG=Suche&meta=) :(
My imdb.pl looks like this:
```
#!/usr/bin/perl -w

#
# This perl script is intended to perform movie data lookups based on
# the popular www.imdb.com website
#
# For more information on MythVideo's external movie lookup mechanism, see
# the README file in this directory.
#
# Author: Tim Harvey (tharvey AT alumni.calpoly DOT edu)
# Modified: Andrei Rjeousski
# v1.1
# - Added amazon.com covers and improved handling for imdb posters
# v1.2
#     - when searching amazon, try searching for main movie name and if nothing
#       is found, search for informal name
#     - better handling for amazon posters, see if movie title is a substring
#       in the search results returned by amazon
#     - fixed redirects for some movies on impawards
# v1.3
#     - fixed search for low res images (imdb changed the page layout)
#     - added cinemablend poster search
#     - added nexbase poster search
#     - removed amazon.com searching for now

# changes:
# 10-26-2007:
#   Added release date (in ISO 8601 form) to output
# 9-10-2006: Anduin Withers
#   Changed output to utf8

use LWP::Simple;      # libwww-perl providing simple HTML get actions
use HTML::Entities;
use URI::Escape;

eval "use DateTime::Format::Strptime"; my $has_date_format = $@ ? 0 : 1;

use vars qw($opt_h $opt_r $opt_d $opt_i $opt_v $opt_D $opt_M $opt_P);
use Getopt::Std;

$title = "IMDB Query";
$version = "v1.3.5";
$author = "Tim Harvey, Andrei Rjeousski";

my @countries = qw(USA UK Canada Japan);

binmode(STDOUT, ":utf8");

# display usage
sub usage {
   print "usage: $0 -hdrviMPD [parameters]\n";
   print "       -h           help\n";
   print "       -d           debug\n";
   print "       -r           dump raw query result data only\n";
   print "       -v           display version\n";
   print "       -i           display info\n";
   print "\n";
   print "       -M [options] <query>    get movie list\n";
   print "               some known options are:\n";
   print "                  type=[fuzy]         looser search\n";
   print "                  from_year=[int]     limit matches to year\n";
   print "                  to_year=[int]       limit matches to year\n";
   print "                  sort=[smart]        ??\n";
   print "                  tv=[no|both|only]   limits between tv and movies\n";
   print "               Note: multiple options must be separated by ';'\n";
   print "       -P <movieid>  get movie poster\n";
   print "       -D <movieid>  get movie data\n";
   exit(-1);
}

# display 1-line of info that describes the version of the program
sub version {
   print "$title ($version) by $author\n"
}

# display 1-line of info that can describe the type of query used
sub info {
   print "Performs queries using the www.imdb.com website.\n";
}

# display detailed help
sub help {
   version();
   info();
   usage();
}

sub trim {
   my ($str) = @_;
   $str =~ s/^\s+//;
   $str =~ s/\s+$//;
   return $str;
}

# returns text within 'data' between 'beg' and 'end' matching strings
sub parseBetween {
   my ($data, $beg, $end)=@_; # grab parameters

   my $ldata = lc($data);
   my $start = index($ldata, lc($beg)) + length($beg);
   my $finish = index($ldata, lc($end), $start);
   if ($start != (length($beg) -1) && $finish != -1) {
      my $result = substr($data, $start, $finish - $start);
      # return w/ decoded numeric character references
      # (see http://www.w3.org/TR/html4/charset.html#h-5.3.1)
      decode_entities($result);
      return $result;
   }
   return "";
}

# get Movie Data
sub getMovieData {
   my ($movieid)=@_; # grab movieid parameter
   if (defined $opt_d) { printf("# looking for movie id: '%s'\n", $movieid);}

   my $name_link_pat = qr'<a href="/name/[^"]*">([^<]*)</a>'m;

   # get the search results  page
   my $request = "http://www.imdb.com/title/tt" . $movieid . "/";
   if (defined $opt_d) { printf("# request: '%s'\n", $request); }
   my $response = get $request;
   if (defined $opt_r) { printf("%s", $response); }

   # parse title and year
   my $year = "";
   my $title = parseBetween($response, "<title>", "</title>");
   if ($title =~ m#(.+) \((\d+).*\)#) # Note some years have a /II after them?
   {
      $title = $1;
      $year = $2;
   }
   elsif ($title =~ m#(.+) \(\?\?\?\?\)#)
   {
      $title = $1;
   }

   # parse director
   my $data = parseBetween($response, ">Director:</h5>", "</div>");
   if (!length($data)) {
      $data = parseBetween($response, ">Directors:</h5>", "</div>");
   }
   my $director = join(",", ($data =~ m/$name_link_pat/g));

   # parse writer
   # (Note: this takes the 'first' writer, may want to include others)
   $data = parseBetween($response, ">Writers <a href=\"/wga\">(WGA)</a>:</h5>", "</div>");
   if (!length($data)) {
         $data = parseBetween($response, ">Writer:</h5>", "</div>");
   }
   if (!length($data)) {
         $data = parseBetween($response, ">Writers:</h5>", "</div>");
   }
   my $writer = join(",", ($data =~ m/$name_link_pat/g));

   # parse release date
   my $releasedate = '';
   if ($has_date_format) {
      my $dtp = new DateTime::Format::Strptime(pattern => '%d %b %Y',
         on_error => 'undef');
      my $dt = $dtp->parse_datetime(parseBetween($response,
            ">Release Date:</h5> ", "<a "));
      if (defined($dt)) {
         $releasedate = $dt->strftime("%F");
      }
   }

   # parse plot
   my $plot = parseBetween($response, ">Plot Outline:</h5> ", "</div>");
   if (!$plot) {
      $plot = parseBetween($response, ">Plot Summary:</h5> ", "</div>");
   }
   if (!$plot) {
      $plot = parseBetween($response, ">Plot:</h5>", "</div>");
   }

   if ($plot) {
      # replace name links in plot (example 0388795)
      $plot =~ s/$name_link_pat/$1/g;

      # replace title links
      my $title_link_pat = qr!<a href="/title/[^"]*">([^<]*)</a>!m;
      $plot =~ s/$title_link_pat/$1/g;

      # plot ends at first remaining link
      my $plot_end = index($plot, "<a ");
      if ($plot_end != -1) {
         $plot = substr($plot, 0, $plot_end);
      }
      $plot = trim($plot);
   }

   # parse user rating
   my $userrating = parseBetween($response, ">User Rating:</b>", "</b>");
   $userrating = parseBetween($userrating, "<b>", "/");

   # parse MPAA rating
   my $ratingcountry = "USA";
   my $movierating = trim(parseBetween($response, ">MPAA</a>:</h5>", "</div>"));
   if (!$movierating) {
       $movierating = parseBetween($response, ">Certification:</h5>", "</div>");
       $movierating = parseBetween($movierating, "certificates=$ratingcountry",
                                   "/a>");
       $movierating = parseBetween($movierating, ">", "<");
   }

   # parse movie length
   my $rawruntime = trim(parseBetween($response, ">Runtime:</h5>", "</div>"));
   my $runtime = trim(parseBetween($rawruntime, "", " min"));
   for my $country (@countries) {
      last if ($runtime =~ /^-?\d/);
      $runtime = trim(parseBetween($rawruntime, "$country:", " min"));
   }

   # parse cast
   #  Note: full cast would be from url:
   #    www.imdb.com/title/<movieid>/fullcredits
   my $cast = "";
   $data = parseBetween($response, "Cast overview, first billed only",
                               "/table>");
   if (!$data) {
       $data = parseBetween($response, "Series Cast Summary",
                               "/table>");
   }

   if (!$data) {
       $data = parseBetween($response, "Complete credited cast",
                               "/table>");
   }

   if ($data) {
      $cast = join(',', ($data =~ m/$name_link_pat/g));
      $cast = trim($cast);
   }


   # parse genres
   my $lgenres = "";
   $data = parseBetween($response, "<h5>Genre:</h5>","</div>");
   if ($data) {
      my $genre_pat = qr'/Sections/Genres/(?:[a-z ]+/)*">([^<]+)<'im;
      $lgenres = join(',', ($data =~ /$genre_pat/g));
   }

   # parse countries
   $data = parseBetween($response, "Country:</h5>","</div>");
   my $country_pat = qr'/Sections/Countries/[A-Z]+/">([^<]+)</a>'i;
   my $lcountries = trim(join(",", ($data =~ m/$country_pat/g)));

   # output fields (these field names must match what MythVideo is looking for)
   print "Title:$title\n";
   print "Year:$year\n";
   print "ReleaseDate:$releasedate\n";
   print "Director:$director\n";
   print "Plot:$plot\n";
   print "UserRating:$userrating\n";
   print "MovieRating:$movierating\n";
   print "Runtime:$runtime\n";
   print "Writers: $writer\n";
   print "Cast:$cast\n";
   print "Genres: $lgenres\n";
   print "Countries: $lcountries\n";
}

# dump Movie Poster
sub getMoviePoster {
   my ($movieid)=@_; # grab movieid parameter
   if (defined $opt_d) { printf("# looking for movie id: '%s'\n", $movieid);}

   # get the search results  page
   my $request = "http://www.imdb.com/title/tt" . $movieid . "/posters";
   if (defined $opt_d) { printf("# request: '%s'\n", $request); }
   my $response = get $request;
   if (defined $opt_r) { printf("%s", $response); }

   if (!defined $response) {return;}

   my $uri = "";

   # look for references to impawards.com posters - they are high quality
   my $site = "http://www.impawards.com";
   my $impsite = parseBetween($response, "<a href=\"".$site, "\">".$site);

   # jersey girl fix
   $impsite = parseBetween($response, "<a href=\"http://impawards.com","\">http://impawards.com") if ($impsite eq "");

   if ($impsite) {
      $impsite = $site . $impsite;

      if (defined $opt_d) { print "# Searching for poster at: ".$impsite."\n"; }
      my $impres = get $impsite;
      if (defined $opt_d) { printf("# got %i bytes\n", length($impres)); }
      if (defined $opt_r) { printf("%s", $impres); }

      # making sure it isnt redirect
      $uri = parseBetween($impres, "0;URL=..", "\">");
      if ($uri ne "") {
         if (defined $opt_d) { printf("# processing redirect to %s\n",$uri); }
         # this was redirect
         $impsite = $site . $uri;
         $impres = get $impsite;
      }

      # do stuff normally
      $uri = parseBetween($impres, "<img SRC=\"posters/", "\" ALT");
      # uri here is relative... patch it up to make a valid uri
      if ($uri =~ /\.(jpe?g|gif|png)$/) {
          if (!($uri =~ /http:(.*)/ )) {
             my $path = substr($impsite, 0, rindex($impsite, '/') + 1);
             $uri = $path."posters/".$uri;
          }
          if (defined $opt_d) { print "# found ipmawards poster: $uri\n"; }
      }
      else {
          $uri = "";
      }
   }

   # try looking on nexbase
   if ($uri eq "" && $response =~ m/<a href="([^"]*)">([^"]*?)nexbase/i) {
      if ($1 ne "") {
         if (defined $opt_d) { print "# found nexbase poster page: $1 \n"; }
         my $cinres = get $1;
         if (defined $opt_d) { printf("# got %i bytes\n", length($cinres)); }
         if (defined $opt_r) { printf("%s", $cinres); }

         if ($cinres =~ m/<a id="photo_url" href="([^"]*?)" ><\/a>/i) {
            if (defined $opt_d) { print "# nexbase url retreived\n"; }
            $uri = $1;
         }
      }
   }

   # try looking on cinemablend
   if ($uri eq "" && $response =~ m/<a href="([^"]*)">([^"]*?)cinemablend/i) {
      if ($1 ne "") {
         if (defined $opt_d) { print "# found cinemablend poster page: $1 \n"; }
         my $cinres = get $1;
         if (defined $opt_d) { printf("# got %i bytes\n", length($cinres)); }
         if (defined $opt_r) { printf("%s", $cinres); }
        if ($cinres =~ m#<img\b[^>]+\bsrc="(/images/reviews/[^"]*?)"#i) {
            if (defined $opt_d) { print "# cinemablend url retreived\n"; }
            $uri = "http://www.cinemablend.com/".$1;
         }
      }
   }

   # if the impawards site attempt didn't give a filename grab it from imdb
   if ($uri eq "") {
       if (defined $opt_d) { print "# looking for imdb posters\n"; }
       my $host = "http://posters.imdb.com/posters/";

       $uri = parseBetween($response, $host, "\"><td><td><a href=\"");
       if ($uri ne "") {
           $uri = $host.$uri;
       } else {
          if (defined $opt_d) { print "# no poster found\n"; }
       }
   }



   my @movie_titles;
   my $found_low_res = 0;
   my $k = 0;

   # no poster found, take lowres image from imdb
   if ($uri eq "") {
      if (defined $opt_d) { print "# looking for lowres imdb posters\n"; }
      my $host = "http://www.imdb.com/title/tt" . $movieid . "/";
      $response = get $host;

      # Better handling for low resolution posters
      #
      if ($response =~ m/<a name="poster".*<img.*src="([^"]*).*<\/a>/ig) {
         if (defined $opt_d) { print "# found low res poster at: $1\n"; }
         $uri = $1;
         $found_low_res = 1;
      } else {
         if (defined $opt_d) { print "# no low res poster found\n"; }
         $uri = "";
      }

      if (defined $opt_d) { print "# starting to look for movie title\n"; }

      # get main title
      if (defined $opt_d) { print "# Getting possible movie titles:\n"; }
      $movie_titles[$k++] = parseBetween($response, "<title>", "<\/title>");
      if (defined $opt_d) { print "# Title: ".$movie_titles[$k-1]."\n"; }

      # now we get all other possible movie titles and store them in the titles array
      while($response =~ m/>([^>^\(]*)([ ]{0,1}\([^\)]*\)[^\(^\)]*[ ]{0,1}){0,1}\(informal title\)/g) {
         $movie_titles[$k++] = trim($1);
         if (defined $opt_d) { print "# Title: ".$movie_titles[$k-1]."\n"; }
      }

   }

   print "$uri\n";
}

# dump Movie list:  1 entry per line, each line as 'movieid:Movie Title'
sub getMovieList {
   my ($filename, $options)=@_; # grab parameters

   # If we wanted to inspect the file for any reason we can do that now

   #
   # Convert filename into a query string
   # (use same rules that Metadata::guesTitle does)
   my $query = $filename;
   $query = uri_unescape($query);  # in case it was escaped
   # Strip off the file extension
   if (rindex($query, '.') != -1) {
      $query = substr($query, 0, rindex($query, '.'));
   }
   # Strip off anything following '(' - people use this for general comments
   if (rindex($query, '(') != -1) {
      $query = substr($query, 0, rindex($query, '('));
   }
   # Strip off anything following '[' - people use this for general comments
   if (rindex($query, '[') != -1) {
      $query = substr($query, 0, rindex($query, '['));
   }

   # IMDB searches do better if any trailing ,The is left off
   $query =~ /(.*), The$/i;
   if ($1) { $query = $1; }

   # prepare the url
   $query = uri_escape($query);
   if (!$options) { $options = "" ;}
   if (defined $opt_d) {
      printf("# query: '%s', options: '%s'\n", $query, $options);
   }

   # get the search results  page
   #    some known IMDB options are:
   #         type=[fuzy]         looser search
   #         from_year=[int]     limit matches to year (broken at imdb)
   #         to_year=[int]       limit matches to year (broken at imdb)
   #         sort=[smart]        ??
   #         tv=[no|both|only]   limits between tv and movies (broken at imdb)
   #$options = "tt=on;nm=on;mx=20";  # not exactly clear what these options do
   my $request = "http://www.imdb.com/find?q=$query;$options";
   if (defined $opt_d) { printf("# request: '%s'\n", $request); }
   my $response = get $request;
   if (defined $opt_r) {
      print $response;
      exit(0);
   }

   # check to see if we got a results page or a movie page
   #    looking for 'add=<movieid>" target=' which only exists
   #    in a movie description page
   my $movienum = parseBetween($response, "add=", "\" ");
   if (!$movienum) {
      $movienum = parseBetween($response, ";add=", "'");
   }
   if ($movienum) {
      if ($movienum !~ m/^[0-9]+$/) {
         if (defined $opt_d) {
            printf("# Error: IMDB movie number ($movienum), isn't.\n");
         }
         exit(0);
      }

      if (defined $opt_d) { printf("# redirected to movie page\n"); }
      my $movietitle = parseBetween($response, "<title>", "</title>");
      $movietitle =~ m#(.+) \((\d+)\)#;
      $movietitle = $1;
      print "$movienum:$movietitle\n";
      exit(0);
   }

   # extract possible matches
   #    possible matches are grouped in several catagories:
   #        exact, partial, and approximate
   my $popular_results = parseBetween($response, "<b>Popular Titles</b>",
                                              "</table>");
   my $exact_matches = parseBetween($response, "<b>Titles (Exact Matches)</b>",
                                              "</table>");
   my $partial_matches = parseBetween($response, "<b>Titles (Partial Matches)</b>",
                                              "</table>");
#   my $approx_matches = parseBetween($response, "<b>Titles (Approx Matches)</b>",
#                                               "</table>");
   # parse movie list from matches
   my $beg = "<tr>";
   my $end = "</tr>";
   my $count = 0;
   my @movies;

#   my $data = $exact_matches.$partial_matches;
   my $data = $popular_results.$exact_matches;
   # resort to partial matches if no exact
   if ($data eq "") { $data = $partial_matches; }
   # resort to approximate matches if no exact or partial
#   if ($data eq "") { $data = $approx_matches; }
   if ($data eq "") {
      if (defined $opt_d) { printf("# no results\n"); }
      return;
   }
   my $start = index($data, $beg);
   my $finish = index($data, $end, $start);
   my $year;
   my $type;
   my $title;
   while ($start != -1 && $start < length($data)) {
      $start += length($beg);
      my $entry = substr($data, $start, $finish - $start);
      $start = index($data, $beg, $finish + 1);
      $finish = index($data, $end, $start);

      my $title = "";
      my $year = "";
      my $type = "";
      my $movienum = "";

      # Some titles are identical, IMDB indicates this by appending /I /II to
      # the release year.
      #   e.g. "Mon meilleur ami" 2006/I vs "Mon meilleur ami" 2006/II
      if ($entry =~ m/<a href="\/title\/tt(\d+)\/.*\">(.+)<\/a> \((\d+)\/?[a-z]*\)(?: \((.+)\))?/i) {
          $movienum = $1;
          $title = $2;
          $year = $3;
          $type = $4 if ($4);
      } else {
           if (defined $opt_d) {
               print("Unrecognized entry format ($entry)\n");
           }
           next;
      }

      my $skip = 0;

      # fix broken 'tv=no' option
      if ($options =~ /tv=no/) {
         if ($type eq "TV") {
            if (defined $opt_d) {printf("# skipping TV program: %s\n", $title);}
            $skip = 1;
         }
      }
      if ($options =~ /tv=only/) {
         if ($type eq "") {
            if (defined $opt_d) {printf("# skipping Movie: %s\n", $title);}
            $skip = 1;
         }
      }
      # fix broken 'from_year=' option
      if ($options =~ /from_year=(\d+)/) {
         if ($year < $1) {
            if (defined $opt_d) {printf("# skipping b/c of yr: %s\n", $title);}
            $skip = 1;
         }
      }
      # fix broken 'to_year=' option
      if ($options =~ /to_year=(\d+)/) {
         if ($year > $1) {
            if (defined $opt_d) {printf("# skipping b/c of yr: %s\n", $title);}
            $skip = 1;
         }
      }

      # option to strip out videos (I think that's what '(V)' means anyway?)
      if ($options =~ /video=no/) {
         if ($type eq "V") {
            if (defined $opt_d) {
                printf("# skipping Video program: %s\n", $title);
            }
            $skip = 1;
         }
      }

      # (always) strip out video game's (why does IMDB give these anyway?)
      if ($type eq "VG") {
         if (defined $opt_d) {printf("# skipping videogame: %s\n", $title);}
         $skip = 1;
      }

      # add to array
      if (!$skip) {
          my $moviename = $title;
          if ($year ne "") {
              $moviename .= " ($year)";
          }

#         $movies[$count++] = $movienum . ":" . $title;
         $movies[$count++] = $movienum . ":" . $moviename;
      }
   }

   # display array of values
   for $movie (@movies) { print "$movie\n"; }
}

#
# Main Program
#

# parse command line arguments
getopts('ohrdivDMP');

# print out info
if (defined $opt_v) { version(); exit 1; }
if (defined $opt_i) { info(); exit 1; }

# print out usage if needed
if (defined $opt_h || $#ARGV<0) { help(); }

if (defined $opt_D) {
   # take movieid from cmdline arg
   $movieid = shift || die "Usage : $0 -D <movieid>\n";
   getMovieData($movieid);
}

elsif (defined $opt_P) {
   # take movieid from cmdline arg
   $movieid = shift || die "Usage : $0 -P <movieid>\n";
   getMoviePoster($movieid);
}

elsif (defined $opt_M) {
   # take query from cmdline arg
   $options = shift || die "Usage : $0 -M [options] <query>\n";
   $query = shift;
   if (!$query) {
      $query = $options;
      $options = "";
   }
   getMovieList($query, $options);
}
# vim: set expandtab ts=3 sw=3 :
```

I have two ideas: Maybe my script is wrong (could anybody please post a working script??) or there could be a problem with the permissions of the posters directory!? What would you say?

Thanks in advance

Stevi.

---

### Post by Chancey on 2008-11-28
I am having the exact same problem.  Did you wind up finding a solution?

imdb.pl was working fine on 8.04 but I rebuilt the system and installed 8.10, and now I can't fetch posters (same error: A poster exists for this item but could not be retrieved within the timeout period).  

I have tried switching imdb.pl out for the newer SVN script, but that also fails (in a much more glorious manner).

Additionally running imdb.pl in command returns a valid url for the posters, and permissions are set properly on the folder for poster storage.

Anyone have the same problem or know of a solution?

---

### Post by Chancey on 2008-11-28
Sorry, digging a little more I'm getting posters returned from older imdb entries (ie 1980's and prior) but not more recent films.  imdb.pl returns images from two different urls, and it seems that the latter is giving mythvideo problems. Both are valid urls.

```

~$ /usr/share/mythtv/mythvideo/scripts/imdb.pl -P 0080339
http://posters.imdb.com/posters/a/airplane1980_21734.jpg

~$ /usr/share/mythtv/mythvideo/scripts/imdb.pl -P 0450385
http://ia.media-imdb.com/images/M/MV5BMTIwOTUxMzA2NF5BMl5BanBnXkFtZTcwMDAwMDU1MQ@@._V1._SX100_SY131_.jpg

```

---

### Post by Chancey on 2008-11-28
Also, sorry for the rapid series of posts... I'm just trying to preempt the (hopefully) inevitable questions.

Here are the results of running imdb.pl with the debug option:
```

~$ /usr/share/mythtv/mythvideo/scripts/imdb.pl -d -P 0450385
# looking for movie id: '0450385'
# request: 'http://www.imdb.com/title/tt0450385/posters'
# looking for imdb posters
# no poster found
# looking for lowres imdb posters
# found low res poster at: http://ia.media-imdb.com/images/M/MV5BMTIwOTUxMzA2NF5BMl5BanBnXkFtZTcwMDAwMDU1MQ@@._V1._SX100_SY131_.jpg
# starting to look for movie title
# Getting possible movie titles:
# Title: 1408 (2007)
http://ia.media-imdb.com/images/M/MV5BMTIwOTUxMzA2NF5BMl5BanBnXkFtZTcwMDAwMDU1MQ@@._V1._SX100_SY131_.jpg

```

---

### Post by ahood on 2008-11-28
Covers have been inconsistent for me too. I am running Mythbuntu based on gutsy (7.10). I was getting posters, but not for the last 6 imports. I have resorted to creating my own covers, which works well enough. Although it is more convenient just to get it automatically.

I will report more as I learn more.

---

### Post by peloy on 2008-11-29
The Myth developers are aware of the problem, or at least there is a bug for this problem in their bug tracking system:

[http://svn.mythtv.org/trac/ticket/5936](http://svn.mythtv.org/trac/ticket/5936)

There are two proposed patches in there but it doesn't seem like one of those will be the fix that will be implemented. Apparently the code that fetches the posters needs to be changed to follow HTTP redirects.

I got bitten by this problem today and since I don't download posters very often I just manually downloaded the posters that I needed.

Cheers!

---

### Post by t3chn0b0y on 2008-11-29
I tend to get my posters from another source..and the data from IMDB,
I find the posters there way too small and when stretched they look aweful.
It also appears as if they have changed the way the pictures are displayed
on their site? using flash?

---

### Post by hopelessone on 2008-12-06
OK you need to change the folder where the posters are kept, to something say in your home directory... restart mythtv and voilla!!

---

### Post by t3chn0b0y on 2008-12-06
there are plans to use [http://themoviedb.org/]("http://themoviedb.org/"),
the development can be found here [http://svn.mythtv.org/trac/ticket/5917]("http://svn.mythtv.org/trac/ticket/5917").. 

There is an issue with the IMDB terms of service, that states that their
website not be scraped by bots. So as I understand it the IMDB scraper 
will no longer be updated in future versions, themoviedb.org taking its place..

just wanted to add that I have read posts on here saying to not post messages pertaining to the scraping of microsoft for tv guide listings because of their terms of service, so why is it okay to post about IMDB?  Just food for thought.. so its okay to do it as long as its not a competing operating system? LOL...

---

### Post by Chancey on 2009-05-19
The best fix seems to be to switch from imdb to tmdb... I had great success with these directions:
[http://www.mythtv.org/wiki/Tmdb.pl](http://www.mythtv.org/wiki/Tmdb.pl)

---

### Post by Lester_Burnham on 2009-05-31
Hi,

It will work if you go to the posters folder in /var/lib/mythtv/posters and change the permissions to give the group mythtv read/write permissions.
To have the cover art show up in mythweb, you also need to fix that link in 9.04
> sudo ln -s /var/lib/mythtv/posters /var/www/mythweb/data/video_covers

Lester

---

### Post by jimbo1954 on 2009-06-11
Guys,
Any further inputs on this? I'm running Ubuntu 9.04 on an AMD-Athlon based rig. nothing clever, everything other than the LIRC subsystem was done using apt-get, so should be OK. Everything works, I even have both Video AND sound working over the HDMI port :p , but I cannot get MythVideo to grab the posters from IMDB. ](*,)

From Video Manager, I can download the textual information for the video (date/director/plot, etc), and it *tells* me that its downloading the poster (no error message, nothing in syslog or any other log that I can see), but I get nothing when I browse/list the videos except notification that there is "No Image". 

If I run imdb.pl manually in a terminal window with a good IMDB number, it outputs a URL which points to the right poster. I don't get a poster download occurring when MythTV Frontend attempts it (nothing appears in the poster directory). I have checked permissions, and chmod'ed some directories to 777 to confirm that its not a permissions issue.

I have tried redirecting the posters to a different directory (off the home directory of the user initiating MythTV Frontend, as described here and elsewhere). 

I tried changing imdb to tmdb, but got such a rash or errors from MythFrontend that I chickened out :(

Google has failed me this time, so has anyone got any ideas?

Whoa! Wait a minute! I just tried some more debugging, and got this in the frontend log:

"2009-06-11 21:16:44.257 Poster Query: Executing '/usr/share/mythtv/mythvideo/scripts/imdb.pl -P 0058150'
2009-06-11 21:16:46.257 [http://ia.media-imdb.com/images/M/MV...100_SY137_.jpg](http://ia.media-imdb.com/images/M/MV...100_SY137_.jpg)

2009-06-11 21:16:46.257 Copying 'http://ia.media-imdb.com/images/M/MV5BMTc0MDAzMDk1Ml5BMl5BanBnXkFtZTcwMjY4MDE0MQ@@._V1._SX100_SY137_.jpg' -> '/home/jim/posters/0058150.jpg'...
2009-06-11 21:16:46.259 dest_file = /home/jim/posters/0058150.jpg
2009-06-11 21:16:46.338 Get: The operation has been processed but an error occurred.: 400 Bad Request"

But what is an error 400 Bad request???...its not to do with the web query, as the command "/usr/share/mythtv/mythvideo/scripts/imdb.pl -P 0058150" runs clean in a terminal window owned by the MythFrontend initiator user....

Any Clues??

Thanks 

Jim

---

### Post by ctpaterson on 2009-06-13
> **jimbo1954 said:**
> Guys,
Any further inputs on this? I'm running Ubuntu 9.04 on an AMD-Athlon based rig. nothing clever, everything other than the LIRC subsystem was done using apt-get, so should be OK. Everything works, I even have both Video AND sound working over the HDMI port :p , but I cannot get MythVideo to grab the posters from IMDB. ](*,)

From Video Manager, I can download the textual information for the video (date/director/plot, etc), and it *tells* me that its downloading the poster (no error message, nothing in syslog or any other log that I can see), but I get nothing when I browse/list the videos except notification that there is "No Image". 


I saw the exact same behaviour.  I ended up running the tmdb instructions from the above post.  Care to post what errors you saw?  I ssh'd into my myth box, and copied and pasted the commands from the webpage into the terminal window.  I used the non-svn version of things.

One thing I had to do that was not described on the page; I had to go to /usr/share/mythtv/mythvideo/scripts and add executable permissions to the tmdb.pl script.

I generally dislike the approach of fixing a bug with one thing by installing a completely separate thing - but since it does seem that myth is going to be moving in this direction, I figure we may as well get on board.

Cheers.

---

