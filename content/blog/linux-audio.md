+++
date = "2021-05-29"
draft = false
title = "Linux audio"
tags = ["audio", "technology", "Linux", "Debian"]
+++

This is my small rant/ramble about my recent experience with Linux audio. **Warning to the reader**: *I am not claiming there is anything of interest in the following - just getting it off my chest.*

I have been a Linux user since about 2000 or so, having performed countless installs.  With few exceptions--I did waver from the path from about 2005 to 2007--I have always relied on Linux for my primary home/personal computing needs.

I jumped from preferring Fedora to Debian due to the GNOME debacle, and now for many years have been relying on Debian stable + XFCE for stability, predictability, and straightforward performance without any weirdness getting in the way.

However, it still amazes me that there is **always** something that goes slightly awry during installation that needs to be tweaked.

In the old days, there were hairy moments with video, tweaking the X settings manually until the right combo came up.  That is really terrifying when you are wondering if the system whose OS you just overwrote with Linux will ever be functional.  But, ultimately, everything always worked out.

My most recent system had a persistent quirk that I was never able to fix (or never bothered to fix) that came about due to switching back and forth between NVidia and Nouveau drivers. Afterwards, during a restart I always had to manually type a couple of things that remained a minor annoyance. 

I have decided to say goodbye to proprietary graphics setups entirely as a result. NVidia has always been highly disappointing with their attitude towards Linux.  This time around, I bought a chip with Intel HD graphics included and have not looked back.

Anyway, on to the latest story. I was delighted to see that after assembling my latest system and installing Debian 10 (Buster), that everything booted flawlessly, the graphics ran beautifully in HD, and all seemed to be going well.  Until I tried to play one of my favorite videos on YouTube.

**No Sound!**

Well, that was disappointing, but I thought it would not be hard to fix. First I tried some basic efforts like installing the sound control in my tool bar, but that didn't help.  I was a little worried that my motherboard audio support wasn't working.  I then guessed that part of the problem was that I had my USB microphone plugged in during the initial setup.  I needed to reset the default sink. Somehow I couldn't manage this is alsa, but I could in pulse with the command:

> pactl set-default-sink 'alsa_output.pci-0000_00_1f.3.analog-stereo' 

After this, I could play .wav and .mp3 files directly from my system, but my YouTube in Firefox was still not working.

I thought it might be a codec issue with Firefox, and so installed a whole bunch of packages hoping for codec support (libffms, libmediainfo, libogmrip, ccextractor, handbrake, ffcvt, and a bunch of libav* packages with "extra" in the title).  Rebooted a few times along the way too.

But still no dice! 

All along this process, I had been searching online for various tips to help with this issue. Finally I found a suggestion to use **pavucontrol**. Although I couldn't see or control it in the toolbar audio control, pavucontrol showed me that Firefox was muted.  And unmuting was all I needed to do.

I was relieved to have a fully functional system, but I do sometimes find the Linux world really a bit wacko at times.  For advanced operations and specialized packages, you can usually find a good and authoritative source of documentation and help.  And it is great that you can pretty much always find a fix by tinkering with your system. But for the really low-level stuff (as used to happen with video for me, and now audio), there is nothing comprehensive to rely on, only a wilderness of Q&A's from those having trouble in the past.  

Note: Debian is great, but the audio documentation there was very vague and general. Really there should be something akin to "to set up audio on your flavor of Linux, install packages A, B, and C, and check settings x, y, and z.  One can hope for the future.

In the end, it was only two small settings changes that kept me soundless, but it took a couple of hours or more to figure this out.  I am still not sure why Firefox would be muted by default.

With all that said, **Long live Linux!**  I greatly prefer having an OS that I am in control of, rather than one that controls me (MacOS, I am looking at you!).



