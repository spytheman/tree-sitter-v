# tree-sitter-v
V language grammar for [tree-sitter](https://github.com/tree-sitter/tree-sitter)

[![build/test](https://github.com/nedpals/tree-sitter-v/actions/workflows/ci.yml/badge.svg)](https://github.com/nedpals/tree-sitter-v/actions/workflows/ci.yml)

## Existing grammars
This grammar is heavily derived from the following language grammars:

- [tree-sitter-go](https://github.com/tree-sitter/tree-sitter-go)
- [tree-sitter-ruby](https://github.com/tree-sitter/tree-sitter-ruby/)
- [tree-sitter-c](https://github.com/tree-sitter/tree-sitter-c/)

## Installation
```
npm install tree-sitter-v
```

## Usage [(node-tree-sitter)](https://github.com/tree-sitter/node-tree-sitter)
```javascript
const Parser = require('tree-sitter');
const V = require('tree-sitter-v');

const parser = new Parser();
parser.setLanguage(V);
```

## Usage with V [v-tree-sitter (soon)]
```v
// TODO:
import treesitter
import tree_sitter_v.bindings.v

fn main() {
  mut parser := treesitter.new_parser()
  parser.set_language(v.language)
}
```

## Limitations
1. ~~Statements outside functions (aka `vsh`/`script` mode) are not yet supported.~~
2. It does not support all deprecated/outdated syntaxes to avoid any ambiguities and to enforce the one-way philosophy as much as possible.
3. Assembly/SQL code in ASM/SQL block nodes are loosely checked and parsed immediately regardless of the content.
4. ~~Syntaxes related to generics support (e.g template) are not yet implemented.~~

## Node Support (Checked means already been verified and tested)
- [x] AliasTypeDecl (`type_declaration`)
- [x] AnonFn (`fn_literal`)
- [x] ArrayDecompose (`decomposed_element`)
- [x] ArrayFixed (`array_initializer`)
- [x] ArrayInit (`array` / `type_initializer`)
- [x] AsCast (`as_type_cast_expression`)
- [ ] AsmAddressing
- [ ] AsmAlias
- [ ] AsmClobbered
- [ ] AsmDisp
- [ ] AsmIO
- [ ] AsmRegister
- [x] AsmStmt (`asm_statement`. See Limitations[3])
- [ ] AsmTemplate
- [x] AssertStmt (`assert_statement`)
- [x] AssignStmt (`assignment_statement`, `short_var_declaration`)
- [ ] Assoc
- [x] AtExpr (`pseudo_comptime_expression`)
- [x] Attr (`attribute_declaration`)
- [x] Block (`block`)
- [x] BoolLiteral (`true` / `false`)
- [x] BranchStmt (`block` for if / `expression_case` for match)
- [x] CallArg (`argument_list`)
- [x] CallExpr (`call_expression`)
- [x] CastExpr (`type_cast_expression`)
- [x] Chan (`channel_type`)
- [x] ChanInit (`type_initializer`)
- [x] CharLiteral (`rune_literal`)
- [x] Comment (`comment`)
- [x] CompFor (`comptime_for_statement`)
- [x] ComptimeCall (`call_expression` -> `comptime_identifier` as field)
- [x] ComptimeSelector(`selector_expression` -> `comptime_selector_expression` as field)
- [ ] ConcatExpr
- [x] ConstDecl (`const_declaration`)
- [x] ConstField (`const_spec`)
- [x] DeferStmt (`defer_statement`)
- [x] DumpExpr (`call_expression`)
- [x] EmbeddedFile (`call_expression` -> `comptime_identifier` as name)
- [x] EnumDecl (`enum_declaration`)
- [x] EnumField (`enum_member`)
- [x] EnumVal (`enum_identifier`)
- [x] ExprStmt
- [x] FloatLiteral (`float_literal`)
- [x] FnDecl (`function_declaration`)
- [x] FnTypeDecl (`function_type`)
- [x] ForCStmt (`for_statement`: `cstyle_for_clause`)
- [x] ForInStmt (`for_statement`: `in_operator`)
- [x] ForStmt (`for_statement`)
- [x] GlobalDecl (`global_var_declaration`)
- [x] GlobalField (`global_var_declaration` -> `global_var_type_initializer`)
- [x] GoExpr (`go_statement`)
- [x] GotoLabel (`labeled_statement`, `empty_labeled_statement`)
- [x] GotoStmt (`goto_statement`)
- [x] HashStmt (Currently supported: `c_include_clause`, `c_flag_clause`,  `c_define_clause`)
- [x] Ident (`identifier`)
- [x] IfBranch (`if_expression`)
- [x] IfExpr (`if_expression`)
- [x] IfGuardExpr (`if statement`: `is_expression`)
- [x] Import (`import_declaration`)
- [x] ImportSymbol (`import_symbol`)
- [x] IndexExpr (`index_expression` / `slice_expression`)
- [ ] InfixExpr
- [x] IntegerLiteral (`int_literal`)
- [x] InterfaceDecl (`interface_declaration`)
- [x] InterfaceEmbedding (`interface_declaration` -> `type_identifier`)
- [x] Likely (`call_expression`)
- [ ] LockExpr
- [x] MapInit (`type_initializer`)
- [x] MatchBranch (`expression_case`)
- [x] MatchExpr (`match_expression`)
- [x] Module (`module_clause`)
- [x] MultiReturn (`multi_return_type`) (NOTE: shouldn't be used in arguments)
- [x] NodeError (`[ERROR]`)
- [x] None (`none`)
- [x] OffsetOf (`call_expression`)
- [x] OrExpr (`or_block`)
- [x] Param (`parameter_declaration`)
- [x] ParExpr (`parenthesized_expression`)
- [x] PostfixExpr (`inc_statement`, `dec_statement`)
- [ ] PrefixExpr
- [x] RangeExpr (`range`)
- [x] Return (`return_statement`)
- [x] SelectBranch (`select_branch`, `select_default_branch`)
- [x] SelectExpr (`select_expression`, TODO support for `if` and `for`)
- [x] SelectorExpr (`selector_expression`)
- [x] SizeOf (`call_expression`)
- [x] SqlExpr (`sql_expression`. See Limitations[3])
- [x] SqlStmt (`sql_expression`. See Limitations[3])
- [x] SqlStmtLine (`sql_expression`. See Limitations[3])
- [x] StringInterLiteral (`interpreted_string_literal`)
- [x] StringLiteral (`_string_literal`)
- [x] StructDecl (`struct_declaration`)
- [x] StructField (`struct_field_declaration`)
- [x] StructInit (`type_initializer`)
- [x] StructInitEmbed (`decomposed_element`)
- [x] StructInitField (`literal_value`)
- [x] SumTypeDecl (`type_declaration`)
- [x] TypeNode (`type_identifier`)
- [x] TypeOf (`call_expression`)
- [x] UnsafeExpr (`unsafe_expression`)
