#!/bin/sh

cat "$1" | while read line; do
	book=$(echo "$line" | cut -f1)
	chapter=$(echo "$line" | cut -f4)
	verse=$(echo "$line" | cut -f6 | tr "\'" "\`")

	[ "$book" == "$oldbook" ] || echo -n "var TextsRaw = '[[" >> "$book.json"
	[ "$book" == "$oldbook" ] || oldchapter="$chapter" >> "$book.json"
	[ "$chapter" == "$oldchapter" ] || echo -n "\"END OF CHAPTER\"],[" >> "$book.json"

	oldbook="$book"
	oldchapter="$chapter"
	
	echo -n "\"$verse\"," >> "$book.json"
done
