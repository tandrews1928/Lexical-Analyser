The grammar rules for the language “TINY” are listed below. I will identify the tokens in this language and build a lexical analyser (lexer) for recognizing and outputting TINY tokens.

# https://www.cs.rochester.edu/~brown/173/readings/05_grammars.txt
#
#	"TINY" Grammar
#
# PGM	-->	STMT+
# STMT	-->	ASSIGN	|	"print"	EXP
# ASSIGN	-->	ID	"="	EXP
# EXP	-->	TERM	ETAIL
# ETAIL	-->	"+" TERM	ETAIL	| "-" TERM	ETAIL | EPSILON
# TERM	-->	FACTOR	TTAIL
# TTAIL	-->	"*" FACTOR TTAIL	| "/" FACTOR TTAIL | EPSILON
# FACTOR	-->	"(" EXP ")" | INT	| ID
#
# ID	-->	ALPHA+
# ALPHA	-->	a	|	b	| … | z	or
#	A	|	B	| … | Z
# INT	-->	DIGIT+
# DIGIT	-->	0	|	1	| …	|	9
# WHITESPACE -->	Ruby Whitespace

Whenever a token is identified, I encapsulate it using the Token class below. Each token has a type and text. For example, if DOG was identified as a variable in this language, it could have type “id” and
text “DOG”. The add operator might have type “addOp” and text “+” or type “+” and text “+”.  
