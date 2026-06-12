---
title: "Firefox not rendering Devanagari fonts properly"
date: 2008-05-22
forum: Mandriva/Mageia
---

### Post by kagashe on 2008-05-22
Hi,

I started my tryst with Linux in 2004 after buying HP COMPAQ Presario 2500 series Laptop which came with Mandrake Linux 9.1 CDs with HP Logo. I had used it for almost one year. I tried to upgrade to version 10, faced some difficulties and joined Mandrivausers.org forum and received lot of support.

I switched to Ubuntu 5.04 and have been using latest Ubuntu versions.

Recently I bought Linux for You Magazine (published in India) which arrived with Mandriva 2008 on DVD. Although my Laptop does not have DVD drive, I converted the DVD into iso on another machine and transferred the iso on the Laptop and installed.

Since all leading Linux distributions have become heavy for low RAM machines I don't use KDE or Gnome. I have installed Mandriva 2008 Icewm desktop.

I like Mandriva 2008 and may continue to use it provided the problem stated in the Subject line gets resolved.

When I opened Firefox it was not showing any Devanagari characters at all. Then I downloaded ttf-indic fonts from Indlinux website and installed them through Mandriva Control Centre.

After installing the fonts Firefox shows them but the rendering is not correct.

I understand that the Firefox build in Mandriva is pango enabled. I have also checked it by typing about:buildconfig in the address bar.

I have also checked that although I am not using KDE or Gnome the pango support exists in Mandriva since pango version 1.20 and all the libraries are installed.

I don't understand what is missing. Please help.

kagashe

NB: Devanagari is the script for Hindi Language.
I have added Devanagari Keyboard Layout. I can type properly using this keyboard on other applications and the font rendering is ok. Rendering in firefox is the only problem.

Solved as follows:
I solved the problem. I reinstalled Mandriva 2008 and during reinstallation have chosen the required languages. These languages were added as additional languages apart from English. After reinstall I checked the font rendering. Initially it was not working. Then I opened the Regional settings dialogue and changed the default from English to the Indian Language. The font rendering was working now. It seems that the font rendering is somehow linked with default Locales settings.

---

### Post by AdamWill on 2008-05-22
Hi there! sorry for the trouble.

There's a fonts-ttf-devanagari package - is that installed?

Can you take a screenshot to illustrate exactly what's wrong with the Firefox rendering?

Thanks!

---

### Post by kagashe on 2008-05-22
> **AdamWill said:**
> Hi there! sorry for the trouble.

There's a fonts-ttf-devanagari package - is that installed?

Can you take a screenshot to illustrate exactly what's wrong with the Firefox rendering?

Thanks!Yes. The fonts are installed. I have also tried the command to enable Pango. No change.

Yes, I can illustrate. We use [this page]("http://en.wikipedia.org/wiki/Help:Multilingual_support_(Indic)#Check_for_existing_support") on Wikipedia to check the support.

At present I am on Ubuntu Hardy and taken the screenshot of the page and attaching with this post. Compare the columns correct rendering and your computer. Notice that Ubuntu also fails for Sinhala and Tibetan but all Indian languages show correct rendering.

I will reboot into Mandriva 2008 after some time and take the screenshot and attach here. You will know the difference.

kagashe

---

### Post by kagashe on 2008-05-22
I am attaching the screenshot taken on Mandriva 2008. Compare the two columns here. Notice the difference particularly for Devanagari.

kagashe

---

### Post by kagashe on 2008-05-23
I am happy to report that Firefox 3 beta renders the fonts correctly on Mandriva 2008.

kagashe

---

### Post by AdamWill on 2008-05-23
Well, I presume you're using the upstream tarball for Firefox 3, right? If so, then it's *either* a bug in Firefox 2 that's fixed in Firefox 3, *or* it's a difference in how we build Firefox versus how Mozilla builds Firefox.

Could you possibly get the tarball for Firefox 2 from mozilla.org and run that, and compare it to how it looks in Mandriva's Firefox 2 package? Thanks.

For what it's worth, by the way, I see the same bug on my machine (Cooker, with Firefox 2). Webkit-based browsers render it correctly.

---

### Post by kagashe on 2008-05-24
> **AdamWill said:**
> Well, I presume you're using the upstream tarball for Firefox 3, right? If so, then it's *either* a bug in Firefox 2 that's fixed in Firefox 3, *or* it's a difference in how we build Firefox versus how Mozilla builds Firefox.

Could you possibly get the tarball for Firefox 2 from mozilla.org and run that, and compare it to how it looks in Mandriva's Firefox 2 package? Thanks.

For what it's worth, by the way, I see the same bug on my machine (Cooker, with Firefox 2). Webkit-based browsers render it correctly.
1) There is no bug in Firefox 2 (or if it is a bug, it is taken care by the distributions). Ubuntu builds Firefox 2 with --enable pango option and it works in rendering the fonts. Mandriva also builds Firefox 2 with --enable pango option but I found it not working on Mandriva 2008, therefore, reported here and provided the screenshots. Question remains: if it works on Ubuntu why not on Mandriva?

2) I know that if I use the tarballs for Firefox 2 from Mozilla it is neither going to work on Ubuntu, Mandriva or any other Linux distribution because the default build is not pango enabled.

3) Firefox 3 does not need to be built with --enable pango option by Ubuntu, Mandriva or any other Linux distribution for correct rendering of fonts, therefore, it is working. Perhaps a bug in Firefox 2 has been removed.

kagashe

---

### Post by kagashe on 2008-05-26
Problem of rendering in Firefox 2 solved. I have edited the original post and added the solution at the end.

kagashe

---

### Post by AdamWill on 2008-05-26
well, in a sense that's not 'solved', as the fonts should be rendered properly in all locales...

so when it works in Ubuntu you also have the locale set to Indian, and if you set it to English, the rendering breaks?

---

### Post by kagashe on 2008-05-27
> **AdamWill said:**
> well, in a sense that's not 'solved', as the fonts should be rendered properly in all locales...

so when it works in Ubuntu you also have the locale set to Indian, and if you set it to English, the rendering breaks?No. In Ubuntu the rendering works even when the locales are set to English.

In fact majority from India who access internet expect knowledge of English as mandatory and do not like their locales set to English but if they surf web sites with Indian Language fonts they expect it to work.

kagashe

---

### Post by kagashe on 2008-05-27
I recollect one more point regarding pango enabled build of firefox. When Dapper Drake was released some users reported that pango enabled Firefox was slower compared to the build available at Mozilla (which is not built with -enable pango option). The solution was to disable pango support which is supposed to be done on command line.

It is possible that Firefox shipped with Mandriva, although, built with -enable pango may be faster since the pango support does not work till you use the locales.

Anyway,all this may be going to history books with Firefox 3.

kagashe

---

### Post by AdamWill on 2008-05-27
No, we don't disable Pango on the command line, we always have it enabled in order to (hopefully :>) make font rendering work right.

Um. So there's definitely some kind of problem here. If you think we should get it fixed, the best thing to do is file a bug at [http://qa.mandriva.com/](http://qa.mandriva.com/) including all the details we worked out in this thread. Thanks!

---

### Post by kagashe on 2008-05-27
> **AdamWill said:**
> No, we don't disable Pango on the command line, we always have it enabled in order to (hopefully :>) make font rendering work right.

Um. So there's definitely some kind of problem here. If you think we should get it fixed, the best thing to do is file a bug at [http://qa.mandriva.com/](http://qa.mandriva.com/) including all the details we worked out in this thread. Thanks!I went to Mandriva Bugzilla and searched on "Firefox rendering" and found [this bug]("https://qa.mandriva.com/show_bug.cgi?id=35722").

Please read what Frederic Crozat says as final comment:
> unfortunately, pango rendering is slower than firefox main rendering and many
people complained when we enabled pango rendering by default, so it is only
enabled for specific locale.

Marcelo, could you have a look at ubuntu firefox package to see what it their
rationale for enabling / disabling pango ? I think they do the same as we do. Note "it is only enabled for specific locale."

I did not file separate bug but commented on the same bug.

I think that resolves the discussion about how Mandriva enables Firefox rendering.

kagashe

---

### Post by Rrory on 2008-05-28
If I might jump in with a question. I have Devanagari and Gurmukhi enabled and they display perfectly on wiki and websites.But when I go to some web sites, it's just a bunch of Roman letters.Is there anything I can do?

---

### Post by kagashe on 2008-05-28
> **Rrory said:**
> If I might jump in with a question. I have Devanagari and Gurmukhi enabled and they display perfectly on wiki and websites.But when I go to some web sites, it's just a bunch of Roman letters.Is there anything I can do?Some websites do not use UTF-8 fonts but use some embedded fonts which display only on Windows. Here is [an example]("http://sify.com/hindi/").
kagashe

---

### Post by AdamWill on 2008-05-28
Oh, indeed, you're quite right. I was mis-remembering the state of our Firefox packages with regard to Pango rendering. As you say, I was wrong and fcrozat is right, and that's the explanation for the issue.

---

