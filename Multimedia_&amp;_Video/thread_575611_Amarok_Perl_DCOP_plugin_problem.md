---
title: "Amarok Perl DCOP plugin problem"
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by colsinc on 2007-10-14
Hi

I am running Amarok on Xubuntu 7.04.  I am trying to install the [httpremote_amarok]("http://www.kde-apps.org/content/show.php?content=36970") plugin, and it installs fine but produces this error when run 
> The script 'httpremote_amarok.pl' exited with error code: 2
and in 'details'
> Can't locate DCOP/Amarok/Player.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /home/colin/.kde/share/apps/amarok/scripts/httpremote_amarok/httpremote_amarok.pl line 31.
BEGIN failed--compilation aborted at /home/colin/.kde/share/apps/amarok/scripts/httpremote_amarok/httpremote_amarok.pl line 31.
which is pretty much the same error reported by N7DR in the comments on the kde-apps.org page.  Following the advice supplied there, I ended up at the CPAN page for Perl-5.8.2, which I downloaded as a tar.gz .  After unpacking, I ran the install script.  This is where I hit my problem.  This is the output: (P.S. the important bit is right down the bottom;))
> colin@colins-computer:~/Desktop/perl-5.8.0$ sudo sh Configure -e
Password:
 
Beginning of configuration questions for perl5.
 
Checking echo to see how to suppress newlines...
...using \c
The star should be here-->*
 
First let's make sure your kit is complete.  Checking...
Looks good...
 
 
Would you like to see the instructions? [n] 
 
Locating common programs...
awk is in /usr/bin/awk.
cat is in /bin/cat.
chmod is in /bin/chmod.
comm is in /usr/bin/comm.
cp is in /bin/cp.
echo is in /bin/echo.
expr is in /usr/bin/expr.
grep is in /bin/grep.
ls is in /bin/ls.
mkdir is in /bin/mkdir.
rm is in /bin/rm.
sed is in /bin/sed.
sort is in /usr/bin/sort.
touch is in /usr/bin/touch.
tr is in /usr/bin/tr.
uniq is in /usr/bin/uniq.
 
Don't worry if any of the following aren't found...
I don't see Mcc out there, offhand.
ar is in /usr/bin/ar.
I don't see bison out there, either.
I don't see byacc out there, either.
cpp is in /usr/bin/cpp.
I don't see csh out there, either.
date is in /bin/date.
egrep is in /bin/egrep.
I don't see gmake out there, either.
gzip is in /bin/gzip.
less is in /usr/bin/less.
ln is in /bin/ln.
make is in /usr/bin/make.
more is in /bin/more.
nm is in /usr/bin/nm.
nroff is in /usr/bin/nroff.
pg is in /usr/bin/pg.
test is in /usr/bin/test.
uname is in /bin/uname.
zip is in /usr/bin/zip.
Using the test built into your sh.
 
Checking compatibility between /bin/echo and builtin echo (if any)...
They are not compatible!  You are probably running ksh on a non-USG system.
I'll have to use /bin/echo instead of the builtin, since Bourne shell doesn't
have echo built in and we may have to run some Bourne shell scripts.  That
means I'll have to use '-n' to suppress newlines now.  Life is ridiculous.

The star should be here-->*
 
Symbolic links are supported.
 
Checking how to test for symbolic links...
Your builtin 'test -h' may be broken.
Trying external '/usr/bin/test -h'.
You can test for symbolic links with '/usr/bin/test -h'.
 
 
Good, your tr supports [:lower:] and [:upper:] to convert case.
Using [:upper:] and [:lower:] to convert case.

First time through, eh?  I have some defaults handy for some systems
that need some extra help getting the Configure answers right:

3b1           dynixptx       isc           opus          super-ux   
aix           dynix          linux         os2           svr4   
altos486      epix           lynxos        os390         svr5   
amigaos       esix4          machten_2     posix-bc      ti1500   
apollo        fps            machten       powerux       titanos   
atheos        freebsd        mint          qnx           ultrix_4   
aux_3         genix          mips          rhapsody      umips   
beos          gnu            mpc           sco_2_3_0     unicosmk   
bsdos         greenhills     mpeix         sco_2_3_1     unicos   
convexos      hpux           ncr_tower     sco_2_3_2     unisysdynix   
cxux          i386           netbsd        sco_2_3_3     utekv   
cygwin        irix_4         newsos4       sco_2_3_4     uts   
darwin        irix_5         next_3_0      sco           uwin   
dcosx         irix_6_0       next_3        solaris_2     vmesa   
dec_osf       irix_6_1       next_4        stellar       vos   
dgux          irix_6         nonstopux     sunos_4_0   
dos_djgpp     isc_2          openbsd       sunos_4_1   

You may give one or more space-separated answers, or "none" if appropriate.
A well-behaved OS will have no hints, so answering "none" or just "Policy"
is a good thing.  DO NOT give a wrong version or a wrong OS.

Which of these apply, if any? [linux] 

You don't have an ELF gcc.  I will use dld if possible.  If you are
using a version of DLD earlier than 3.2.6, or don't have it at all, you
should probably upgrade. If you are forced to use 3.2.4, you should
uncomment a couple of lines in hints/linux.sh and restart Configure so
that shared libraries will be disallowed.


Disabling ndbm.  This will generate a Whoa There message in Configure.
Read hints/linux.sh for further information.

You appear to have a working bash.  Good.

Configure uses the operating system name and version to set some defaults.
The default value is probably right if the name rings a bell. Otherwise,
since spelling matters for me, either accept the default or answer "none"
to leave it blank.

Operating system name? [linux] 
 
Operating system version? [2.6.20-15-generic] 

Perl can be built to use the SOCKS proxy protocol library.  To do so,
Configure must be run with -Dusesocks.  If you use SOCKS you also need
to use the PerlIO abstraction layer, this will be implicitly selected.

If this doesn't make any sense to you, just accept the default 'n'.
Build Perl for SOCKS? [n] 

Previous version of perl5 used the standard IO mechanisms as
defined in <stdio.h>.  Versions 5.003_02 and later of perl5 allow
alternate IO mechanisms via the PerlIO abstraction layer, but the
stdio mechanism is still available if needed.  The abstraction layer
can use AT&T's sfio (if you already have sfio installed) or regular stdio.
Using PerlIO with sfio may cause problems with some extension modules.

If this doesn't make any sense to you, just accept the default 'y'.
Use the PerlIO abstraction layer? [y] 

Perl can be built to take advantage of threads on some systems.
To do so, Configure can be run with -Dusethreads.

Note that Perl built with threading support runs slightly slower
and uses more memory than plain Perl. The current implementation
is believed to be stable, but it is fairly new, and so should be
treated with caution.

If this doesn't make any sense to you, just accept the default 'n'.
Build a threading Perl? [n] 

Perl can be built so that multiple Perl interpreters can coexist
within the same Perl executable.
 
If this doesn't make any sense to you, just accept the default 'n'.
Build Perl for multiplicity? [n] 
 
Hmm...  Looks kind of like a Version 7 system, but we'll see...
 
Congratulations.  You aren't running Eunice.
 
It's not Xenix...
 
Nor is it Venix...
Use which C compiler? [cc] **/usr/bin/gcc-4.1**
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
Uh-oh, the C compiler '/usr/bin/gcc-4.1' doesn't seem to be working.
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
Uh-oh, the C compiler '/usr/bin/gcc-4.1' doesn't seem to be working.
You need to find a working C compiler.
Either (purchase and) install the C compiler supplied by your OS vendor,
or for a free C compiler try [http://gcc.gnu.org/](http://gcc.gnu.org/)
I cannot continue any further, aborting.


I have cc and gcc installed and as noted in bold had resorted to manually pointing out the location, but Uh-oh, none of the C compilers seem to be working.  

I am really not sure what I am doing wrong here - any help greatly appreciated :)

P.S. P4 3Ghz, 768MB Gigabyte GA-85661FXM-775 nVidia GeForce FX5500 256MB

P.P.S. Well done whoever thought up that 'similar posts' function which appears when one is creating a new post - a very elegant solution.  Unfortunately I could not find help in the suggested posts.  Sorry if this problem is already being discussed.

---

