impulse-response-boosterpack
============================

A boosterpack for Texas Instruments' MSP430 and Stellaris Launchpad
platforms.

The frequency response of a linear system -- be it a simple op amp
circuit or the complex acoustics of a concert hall -- is easy to talk
about but hard to measure.  With this boosterpack, I aim to make the
measurement process a little easier.

What's hard about it?
---------------------

Going from digital to analog to digital
---------------------------------------

Most often, we'd like to have our results in digital form, so we can
plot it, analyze it, and so forth.  That means converting between
analog and digital domains, while avoiding issues such as frequency
aliasing, quantization noise, clipping, and other non-linearities.
The 10- to 12-bit ADCs in the MSP430 and Stellaris Launchpads, while
fine for most uses, will exhibit most of these problems unless you,
the user, take pains to do things right.

That's hard.  You'd need to include anti-aliasing filters, avoid
clipping events, and keep the signal amplitude high enough to control
quantization noise, for starters.  You have to do these things on both
sides:  the ADC side and the DAC side.  Oh, wait... the processors
included with the Launchpads don't have DACs.  

Removing environmental effects
------------------------------

Once past the engineering issues of moving between digital and analog
domains, you're still not home free.  Consider what happens when you
try to measure the frequency response of a loudspeaker.  You drive
your speaker with a pure tone (sine wave), and use a microphone to
record the response.  Sweep the frequency of the sine wave over the
range of interest, and you're there, right?

Unfortunately, no.  The microphone response is mixed in there, too,
but most modern microphones are pretty good.  You can probably live
with the effects of the microphone response.  The real problem is the
room.  Reflections from the walls, floor and ceiling will introduce
huge nulls into your perceived loudspeaker characteristic.  The room
response effectively overwhelms the loudspeaker response in your
measurement.  But you say you don't have access to an anechoic
chamber?



